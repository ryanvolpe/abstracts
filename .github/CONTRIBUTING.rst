How to Contribute
=================

Documentation
-------------

Changelog
^^^^^^^^^

If your change is noteworthy, there needs to be a changelog entry, so our users can learn about it!

To avoid merge conflicts, we use the towncrier_ package to manage our changelog.
``towncrier`` uses independent files for each pull request -- so called *news fragments* -- instead of one monolithic changelog file.
On release those news fragments are compiled into our ``CHANGELOG.rst``.

You don't need to install ``towncrier`` yourself, you just have to abide to a few simple rules:

- For each pull request, add a new file into ``changelog.d`` with a filename adhering to the ``pr#.(change|deprecation|breaking).rst`` schema:
  For example ``changelog.d/42.change.rst`` for a non-breaking change, that is proposed in pull request number 42.
- As with other docs, please use `semantic newlines`_ within news fragments.
- Wrap symbols like modules, functions, or classes into double backticks so they are rendered in a monospaced font.
- If you mention functions or other callables, add parantheses at the end of their names: ``abstr.func()`` or ``abstr.Class.method()``.
  This makes the changelog a lot more readable.
- Prefer simple past or constructions with "now".
  For example:

  + Added ``abstr.validators.func()``.
  + ``abstr.func()`` now doesn't crash the Large Hadron Collider anymore.
- If you want to reference multiple issues, copy the news fragment to another filename.
  ``towncrier`` will merge all news fragments with identical contents into one entry with multiple links to the respective pull requests.

Example entries:

  .. code-block:: rst

     Added ``abstr.validators.func()``.
     The feature really *is* awesome.

or:

  .. code-block:: rst

     ``abstr.func()`` now doesn't crash the Large Hadron Collider anymore.
     The bug really *was* nasty.

----

``tox -e changelog`` will render the current changelog to the terminal if you have any doubts.

.. _towncrier: https://pypi.org/project/towncrier
.. _semantic newlines: http://rhodesmill.org/brandon/2012/one-sentence-per-line/
