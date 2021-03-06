FullContact.py
==============

[![PyPI version](https://badge.fury.io/py/fullcontact.py.svg)](https://pypi.python.org/pypi/FullContact.py)
[![Build Status](https://api.travis-ci.org/fullcontact/fullcontact.py.svg?branch=master)](https://travis-ci.org/fullcontact/fullcontact.py)

A Python interface for the [FullContact API](http://docs.fullcontact.com/).

Installation
------------

```
pip install fullcontact.py
```

Usage
-----


```python
>>> from fullcontact import FullContact
>>> fc = FullContact('your_api_key')

# returns a real requests object
>>> r = fc.person(email='you@email.com')
>>> r.status_code
200
>>> r.headers['x-rate-limit-remaining']
'59'
>>> r.json()
{u'socialProfiles': [...], u'demographics': {...}, ... }

# for batched calls - a list of tuples like (endpoint, {params})
>>> batch_calls = [
        ('disposable', {'email': 'this-is-a-fake-email@fake.com'}),
        ('person', {'email': 'email@gmail.com'}),
        ...
    ]
>>> r2 = fc.api_batch(batch_calls)
```

Tests
-----

A limited test suite is available. Run with `nosetests` after installing, or if
you're installing directly via `setup.py` you can use Nose's setuptools
extension like so:

```
python setup.py install nosetests
```

Support
-------
FullContact.py is tested against Python 2.6, 2.7, 3.3, 3.4, and 3.5
