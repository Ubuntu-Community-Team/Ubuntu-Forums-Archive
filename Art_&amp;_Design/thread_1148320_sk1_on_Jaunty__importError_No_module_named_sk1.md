---
title: "sk1 on Jaunty:  importError: No module named sk1"
date: 2009-05-04
forum: Art &amp; Design
---

### Post by bobdobbs on 2009-05-04
Hi All.

Sk1 looks like a pretty amazing project. It's a vector graphics editing tool. 

I downloaded the .deb from it's main page:
[http://sk1project.org/modules.php?name=Products&product=sk1](http://sk1project.org/modules.php?name=Products&product=sk1)

When I try to run it, I get this:
```

Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named sk1

```

I couldn't find anything on their forums about it.
Neither could I join their forum. They aren't taking registrations anymore.

I'm using a 32 bit system, with Python 2.6.2.

Does anyone know why I might be getting this problem ?

Also, does anyone know anything about the vitality of the sk1 project?

---

### Post by smiley1962 on 2009-05-06
You can find the proper packages in synaptic, just look for uniconvertor :) they are the newest version 1.1.3

---

### Post by bobdobbs on 2009-05-06
> **smiley1962 said:**
> You can find the proper packages in synaptic, just look for uniconvertor :) they are the newest version 1.1.3

Hi Smiley.

I can see uniconvertor in synaptic.
I already have it installed.
In fact, it was looking into uniconvertor that allowed me to discover the sk1 project.

But, I can't see sk1 itself in synaptic.
Is there a repo that I need to add ?

---

### Post by realshams on 2009-05-06
My procedure
```
sudo apt-get install subversion tcl8.5-dev tk8.5-dev python-cairo-dev python-imaging python-reportlab python-liblcms python2.5-dev
```
```
svn co https://sk1.svn.sourceforge.net/svnroot/sk1/trunk/sK1 sK1
```
```
cd sK1
```
 but import code err
```
python setup.py build
```

err  follows

$ python setup.py build
Source tree scan...
MANIFEST.in is created
running build
running build_py
package init file 'src/app/modules/__init__.py' not found (or not a regular file)
package init file 'src/app/tcl/__init__.py' not found (or not a regular file)
package init file 'src/app/modules/__init__.py' not found (or not a regular file)
package init file 'src/app/tcl/__init__.py' not found (or not a regular file)
running build_ext
building 'sk1.app.modules.streamfilter' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -DMAJOR_VERSION=0 -DMINOR_VERSION=9 -I/usr/include/python2.6 -c src/extentions/filter/streamfilter.c -o build/temp.linux-i686-2.6/src/extentions/filter/streamfilter.o
src/extentions/filter/streamfilter.c:24:20: error: Python.h: No such file or directory
In file included from src/extentions/filter/streamfilter.c:26:
src/extentions/filter/filterobj.h:31: error: expected declaration specifiers or '...' before '*' token
src/extentions/filter/filterobj.h:31: error: expected declaration specifiers or '...' before 'PyObject'
src/extentions/filter/filterobj.h:32: error: expected declaration specifiers or '...' before 'size_t'
src/extentions/filter/filterobj.h:32: warning: type defaults to 'int' in declaration of 'size_t'
src/extentions/filter/filterobj.h:32: error: 'size_t' declared as function returning a function
src/extentions/filter/filterobj.h:32: warning: function declaration isn't a prototype
src/extentions/filter/filterobj.h:33: error: expected declaration specifiers or '...' before 'PyObject'
src/extentions/filter/filterobj.h:34: error: 'filter_write_proc' declared as function returning a function
src/extentions/filter/filterobj.h:35: error: expected declaration specifiers or '...' before 'PyObject'
src/extentions/filter/filterobj.h:40: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
src/extentions/filter/filterobj.h:47: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
src/extentions/filter/filterobj.h:55: error: expected ')' before '*' token
src/extentions/filter/filterobj.h:56: error: expected ')' before '*' token
src/extentions/filter/filterobj.h:58: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
src/extentions/filter/filterobj.h:60: error: expected ')' before '*' token
src/extentions/filter/filterobj.h:63: error: expected ')' before '*' token
src/extentions/filter/filterobj.h:64: error: expected ')' before '*' token
src/extentions/filter/filterobj.h:67: error: expected ')' before '*' token
src/extentions/filter/filterobj.h:75: error: expected specifier-qualifier-list before 'PyObject_HEAD'
src/extentions/filter/filterobj.h:92: warning: return type defaults to 'int'
src/extentions/filter/filterobj.h:92: warning: function declaration isn't a prototype
src/extentions/filter/filterobj.h: In function 'DL_IMPORT':
src/extentions/filter/filterobj.h:92: error: expected declaration specifiers before 'FilterType'
src/extentions/filter/filterobj.h:118: error: expected ')' before '*' token
src/extentions/filter/filterobj.h:119: error: expected ';' before 'size_t'
src/extentions/filter/filterobj.h:130: error: storage class specified for parameter 'Filter_Functions'
In file included from src/extentions/filter/streamfilter.c:27:
src/extentions/filter/linefilter.h:29: error: expected declaration specifiers before 'PyObject'
In file included from src/extentions/filter/streamfilter.c:28:
src/extentions/filter/subfilefilter.h:28: error: expected declaration specifiers before 'PyObject'
In file included from src/extentions/filter/streamfilter.c:29:
src/extentions/filter/base64filter.h:28: error: expected declaration specifiers before 'PyObject'
src/extentions/filter/base64filter.h:29: error: expected declaration specifiers before 'PyObject'
In file included from src/extentions/filter/streamfilter.c:30:
src/extentions/filter/stringfilter.h:29: error: expected declaration specifiers before 'PyObject'
In file included from src/extentions/filter/streamfilter.c:31:
src/extentions/filter/nullfilter.h:29: error: expected declaration specifiers before 'PyObject'
src/extentions/filter/nullfilter.h:30: error: expected declaration specifiers before 'PyObject'
In file included from src/extentions/filter/streamfilter.c:32:
src/extentions/filter/hexfilter.h:28: error: expected declaration specifiers before 'PyObject'
src/extentions/filter/hexfilter.h:29: error: expected declaration specifiers before 'PyObject'
In file included from src/extentions/filter/streamfilter.c:38:
src/extentions/filter/binfile.h:28: error: expected declaration specifiers before 'PyObject'
src/extentions/filter/streamfilter.c:41: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'filter_functions'
src/extentions/filter/streamfilter.c:58: error: expected declaration specifiers before ';' token
src/extentions/filter/streamfilter.c:60: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'functions'
src/extentions/filter/streamfilter.c:77: error: expected declaration specifiers before ';' token
src/extentions/filter/streamfilter.c:80: error: expected declaration specifiers before 'DL_EXPORT'
src/extentions/filter/filterobj.h:130: error: declaration for parameter 'Filter_Functions' but no such parameter
src/extentions/filter/filterobj.h:98: error: declaration for parameter '_Filter_Overflow' but no such parameter
src/extentions/filter/filterobj.h:97: error: declaration for parameter '_Filter_Underflow' but no such parameter
src/extentions/filter/streamfilter.c:94: error: expected '{' at end of input
error: command 'gcc' failed with exit status 1

:(

---

### Post by bobdobbs on 2009-05-08
> **bobdobbs said:**
> Hi Smiley.

I can see uniconvertor in synaptic.
I already have it installed.
In fact, it was looking into uniconvertor that allowed me to discover the sk1 project.

But, I can't see sk1 itself in synaptic.
Is there a repo that I need to add ?

Bump

---

### Post by stani on 2009-05-20
I've made packages for Jaunty and Intrepid in my PPA repository:
[http://pythonide.blogspot.com/2009/05/sk1-vector-graphics-editor-is-now.html](http://pythonide.blogspot.com/2009/05/sk1-vector-graphics-editor-is-now.html)

---

