=========
HappyBase
=========

.. py:currentmodule:: happybase

**HappyBase** is a developer-friendly Python__ library to interact with `Apache
HBase`__. HappyBase is designed for use in standard HBase setups, and offers
application developers a Pythonic API to interact with HBase. Below the surface,
HappyBase uses the `Python Thrift library`__ to connect to HBase using its
Thrift__ gateway, which is included in the standard HBase 0.9x releases.

__ http://python.org/
__ http://hbase.apache.org/
__ http://pypi.python.org/pypi/thrift
__ http://thrift.apache.org/


.. note::

   **Do you enjoy HappyBase?** Please consider making a small donation__ to let
   me know you appreciate my work. Thanks!

   __ https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=ZJ9U8DNN6KZ9Q


Example
=======

The example below illustrates basic usage of the library. The :doc:`user guide
<user>` contains many more examples.

::

   import happybase

   connection = happybase.Connection('hostname')
   table = connection.table('table-name')

   table.put('row-key', {'family:qual1': 'value1',
                         'family:qual2': 'value2'})

   row = table.row('row-key')
   print row['family:qual1']  # prints 'value1'

   for key, data in table.rows(['row-key-1', 'row-key-2']):
       print key, data  # prints row key and data for each row

   for key, data in table.scan(row_prefix='row'):
       print key, data  # prints 'value1' and 'value2'

   row = table.delete('row-key')


Core documentation
==================

.. toctree::
   :maxdepth: 2

   installation
   user
   api


Additional documentation
========================

.. toctree::
   :maxdepth: 1

   news
   development
   todo
   faq
   license


External links
==============

* `Online documentation <http://happybase.readthedocs.org/>`_ (Read the Docs)
* `Downloads <http://pypi.python.org/pypi/happybase/>`_ (PyPI)
* `Source code <https://github.com/wbolster/happybase>`_ (Github)


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`


.. vim: set spell spelllang=en:
