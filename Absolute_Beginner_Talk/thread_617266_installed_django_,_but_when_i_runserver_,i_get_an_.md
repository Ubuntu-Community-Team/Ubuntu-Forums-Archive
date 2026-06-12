---
title: "installed django , but when i runserver ,i get an error"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-11-19
Hi i installed

---

### Post by mvanes on 2007-11-19
What's the error message you're getting?

---

### Post by firedancer on 2007-11-19
cannot connect to host

---

### Post by firedancer on 2007-11-30
ok , i got everything running this time and started with the tutorial , 


but now i got this : ```
>>> from django.template import Template
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/var/lib/python-support/python2.5/django/template/__init__.py", line 918, in <module>
    add_to_builtins('django.template.defaultfilters')
  File "/var/lib/python-support/python2.5/django/template/__init__.py", line 915, in add_to_builtins
    builtins.append(get_library(module_name))
  File "/var/lib/python-support/python2.5/django/template/__init__.py", line 904, in get_library
    mod = __import__(module_name, {}, {}, [''])
  File "/var/lib/python-support/python2.5/django/template/defaultfilters.py", line 5, in <module>
    from django.utils.translation import gettext
  File "/var/lib/python-support/python2.5/django/utils/translation/__init__.py", line 3, in <module>
    if settings.USE_I18N:
  File "/var/lib/python-support/python2.5/django/conf/__init__.py", line 28, in __getattr__
    self._import_settings()
  File "/var/lib/python-support/python2.5/django/conf/__init__.py", line 53, in _import_settings
    raise EnvironmentError, "Environment variable %s is undefined." % ENVIRONMENT_VARIABLE
EnvironmentError: Environment variable DJANGO_SETTINGS_MODULE is undefined.

```


is this related to a corrupted django installation perhaps or do i have to change any settings ?
 i read through it, though i'm afraid i'll "corrupt" it even more ,

any suggestions pls, so i can proceed , thank you

---

### Post by rumli on 2008-01-19
Instead of running a python shell directly, you should go to your project directory (i.e., the one that contains manage.py and settings.py) and run:
```

python manage.py shell

```

Then you can do "from django.template import Template" in that shell.

---

