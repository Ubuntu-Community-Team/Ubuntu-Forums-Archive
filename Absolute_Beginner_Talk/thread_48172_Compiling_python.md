---
title: "Compiling python"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by Zaare on 2005-07-11
I've never used Python before. I've only written Java, html and xml code. Anyway, I need to modify a python-file to change a desklet for gdesklets to my liking.
My question is: How do I compile the .py file into a .pyc file?

---

### Post by JaM on 2005-07-11
You can do it in python in the module py_compile
```
import py_compile
py_compile.compile (pyfile, pycfile)
```

But if you do a 
```
help (py_compile.compile)
```
You will see it isn't necessery:
```
compile(file, cfile=None, dfile=None, doraise=False)
    Byte-compile one Python source file to Python bytecode.

    Arguments:

    file:    source filename
    cfile:   target filename; defaults to source with 'c' or 'o' appended
             ('c' normally, 'o' in optimizing mode, giving .pyc or .pyo)
    dfile:   purported filename; defaults to source (this is the filename
             that will show up in error messages)
    doraise: flag indicating whether or not an exception should be
             raised when a compile error is found. If an exception
             occurs and this flag is set to False, a string
             indicating the nature of the exception will be printed,
             and the function will return to the caller. If an
             exception occurs and this flag is set to True, a
             PyCompileError exception will be raised.

    [b]Note that it isn't necessary to byte-compile Python modules for
    execution efficiency -- Python itself byte-compiles a module when
    it is loaded, and if it can, writes out the bytecode to the
    corresponding .pyc (or .pyo) file.[/b]

    However, if a Python installation is shared between users, it is a
    good idea to byte-compile all modules upon installation, since
    other users may not be able to write in the source directories,
    and thus they won't be able to write the .pyc/.pyo file, and then
    they would be byte-compiling every module each time it is loaded.
    This can slow down program start-up considerably.

    See compileall.py for a script/module that uses this module to
    byte-compile all installed files (or all files in selected
    directories).

```

---

### Post by Zaare on 2005-07-11
Oh, cool. thanks a lot. :)

---

