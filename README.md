# stencil
A minimalist template engine for Python

The goal of Stencil is to provide just enough of a template engine in a single file.


## Quick Start

1. Make a directory for our templates:

    $ mkdir tmpl

1. Create a simple template:

    Good morning, {{ name }}!

1. Write a script to use it

    import stencil

    from .utils import escape

    loader = stencil.TemplateLoader(['tmpl/'])

    t = loader['index.html']
    c = stencil.Contxt({'name': 'Ruprect'}, filters={'escape': scape})

    print t.render(c)
    # Should output "Good morning, Rupprect!"

## What it can do

1. Variable rendering

    {{ var.from.context }}

Django style dotted-lookup variables rendering.

Filters are also supported, if passed to the Context.

    {{ foo.bar|escape }}

Filers can take an arbitrary number of arguments:

    {{ foo.bar|mangle:foo.baz,quz,wibble.pencil }}

2. If conditions

No expression support, just simple boolean testing:

    {% if condition %}
    ...
    {% endif %}
    {% if not condition %}
    ...
    {% endif %}


3. For loops

    {% for x in y %}
    ...
    {% endfor %}

This will also inject a 0-based `loopcounter` into the context.

4. Include

    {% include other.tpl %}


Note: the template using include must be loaded using a TemplateLoader.

5. Load

    {% load libname %}

Additional tag types can be loaded.

## Coming soon

6. Template inheritance

    {% extends %}
    {% block %}...{% endblock %}
