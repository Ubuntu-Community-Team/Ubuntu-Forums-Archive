---
title: "PyGTK"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by M i l a d on 2007-02-23
hi,
please help me!
how can i fix this problem!?
```
Traceback (most recent call last):
  File "setup.py", line 206, in ?
    override='src/eggtray/trayicon.override')]
  File "/var/lib/python-support/python2.4/gtk-2.0/dsextras.py", line 415, in __init__
    kwargs['register'], load_types))
  File "/var/lib/python-support/python2.4/gtk-2.0/dsextras.py", line 328, in __new__
    raise NameError("'%s' is not defined\n" % cls.__name__
NameError: 'Template' is not defined

***************************************************************************
Codegen could not be found on your system and is required by the
dsextras.Template and dsextras.TemplateExtension classes. codegen is part
of PyGTK. To use either Template or TemplateExtension, you should also
install PyGTK.
***************************************************************************

```

---

### Post by po0f on 2007-02-23
M i l a d,

```
[font="Courier New"]$ python
Python 2.5 (release25-maint, Feb 16 2007, 18:44:59) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu1)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import dsextras
>>> dir(dsextras)
['BuildExt', 'Extension', 'GLOBAL_INC', 'GLOBAL_MACROS', 'InstallData',
'InstallLib', 'PkgConfigExtension', '**Template**', 'TemplateExtension',
'__builtins__', '__doc__', '__file__', '__name__', 'build_ext',
'codegen_error_message', 'distutils', 'e', 'fnmatch', 'get_m4_define',
'getoutput', 'getstatusoutput', 'have_pkgconfig', 'install_data', 'install_lib',
'list_files', 'os', 'pkgc_version_check', 're', 'string', 'sys',
'template_classes_enabled']
>>> 
[/font]
```

It seems to work here.  What exactly are you trying to do?

---

### Post by M i l a d on 2007-02-23
```
Python 2.4.4c1 (#2, Oct 11 2006, 21:51:02) 
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import dsextras
>>> dir(dsextras)
['BuildExt', 'Extension', 'GLOBAL_INC', 'GLOBAL_MACROS', 'InstallData', 'InstallLib', 'PkgConfigExtension', 'Template', 'TemplateExtension', '__builtins__', '__doc__', '__file__', '__name__', 'build_ext', 'codegen_error_message', 'distutils', 'e', 'fnmatch', 'get_m4_define', 'getoutput', 'getstatusoutput', 'have_pkgconfig', 'install_data', 'install_lib', 'list_files', 'os', 'pkgc_version_check', 're', 'string', 'sys', 'template_classes_enabled']
>>> 

```

---

### Post by po0f on 2007-02-23
M i l a d,

So, again, I ask: **what are you trying to do**?  A "setup.py" script usually means you are trying to install something.  Maybe it's already available in the repos.

---

### Post by M i l a d on 2007-02-23
[http://www.ubuntuforums.org/showthread.php?t=368359&highlight=gsmile](http://www.ubuntuforums.org/showthread.php?t=368359&highlight=gsmile)

---

### Post by po0f on 2007-02-23
M i l a d,

It's possible that this program no longer works.  I noticed that the last update was sometime in 2005.

---

