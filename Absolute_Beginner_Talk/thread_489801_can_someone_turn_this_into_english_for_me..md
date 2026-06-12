---
title: "can someone turn this into english for me."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-07-01
I just DL'd this pdf editor app but now i can't remember how to make it install. i can basically work myself around feisty but i'm lost when it comes to terminal. thanks a ton in advance.

```
PDFedit readme
-----------------

PDFedit is distributed under terms of GNU GPL.
See doc/LICENSE.GPL for full license text.
See doc/AUTHORS for full list of authors and contributors.
For other more detailed documentation, look into "doc" subdirectory.
File doc/user/user_doc.html contain more detailed installation instructions
(in the Installation section) and list of required libraries.

Compilation
-----------
 Run:
  ./configure

 Optionally you can specify prefix (default is /usr/local/) or other parameters.
 Run "./configure --help" to see list of possible configuration parameters.

 After configure succesfully finishes, run "make" in this directory to start
 compilation.

Installation
------------
 To install editor, run
  make install

 INSTALL_ROOT environment variable can be used to install into different
 root directory, which can be useful for example when creating packages
 or if installing into chroot jail.

 Example:
  INSTALL_ROOT=/chroot/pdfedit make install

Cygwin build
------------
PATH in cygwin must contain these three directories
/bin			(most required executables are stashed here)
/usr/X11R6/bin		(some libraries are here)
/usr/lib/qt3/bin	(qmake must be in PATH)

You can use cygwin_build.bat to start the build process
(you will need to set CYGWIN_ROOT in the file first)
This will create the package in /tmp/pdfedit-package
and create pack.bat to pack the package with 7-zip
```

---

### Post by Moop on 2007-07-01
I'm not using Feisty at the moment but I think PDF Editor is available in the repositories. Did you look for it in Add/Remove Programs?  You can also go to Synaptic Package Manager and search for it there. I think you will find it and it's much easier to install programs from those places. :)

---

### Post by thesonisshining on 2007-07-01
that would be alot easier but unfortunately it isn't in either of those.

---

### Post by christhemonkey on 2007-07-01
Its not in the repos for feisty no.


Ok.
To start off with you will need the basic compilation tools:
```
sudo apt-get install build-essential 
```

Then change the terminal into the directory of the package:
```
cd /where/you/downloaded/this/pdfedit/to/pdfedit-0.4/ 
```

Then run:
```
./configure 
```

Then hopefuly that should complete succsefully (if it doesnt please post the full output)

If it is succsefull then run:
```
make 
```

And then(once again if last step was succseful!):
```
sudo make install 
```

---

### Post by Moop on 2007-07-01
I just booted into Feisty and found I was wrong. Sorry about that! You can get the .deb package here. 
[http://www.getdeb.net/app.php?name=PDF+Editor]("http://www.getdeb.net/app.php?name=PDF+Editor")

---

### Post by Aurixious on 2007-07-01
I don't know much about linux but I know you can set the file to execute under properties.  Some apps also need you to install things under root.

---

