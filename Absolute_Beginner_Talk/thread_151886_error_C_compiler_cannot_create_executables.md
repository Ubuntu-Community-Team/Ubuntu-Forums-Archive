---
title: "error: C compiler cannot create executables"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by dunomous on 2006-03-28
The program I'm trying to install is gDesklets. 

Installation Process: 
```

root@user:/home/user/gDesklets-0.35.3# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

I did this as just user access as well. As you can see, it is its latest version of 0.35.3. As this problem occurs here, it also occurs in other programs I've tried to install (specifics I cannot instantly recall). 

If this problem is better fit for the gDesklets forum itself, let me know, I'll be glad to  stop cluttering the forums :D

---

### Post by fannymites on 2006-03-28
You could try apt-get install build-essential which will install all the stuff you need to compile.  Unless you already did that.

---

### Post by dunomous on 2006-03-28
ah! thanks so much. Which command for:

```

checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

```

?

I tried `apt-get install XML::Parser' and was given this:

```

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package XML::Parser

```

I'm not sure what package to get it from.

---

### Post by fannymites on 2006-03-28
Maybe try "apt-get install libxml-parser-perl"

I'm actually using dapper (I keep forgetting) so the package name may possible be different.
If that doesn't work you could try opening synaptic and searching for "xml parser" or "xml perl" but set the search parameter to name (by default it's name and description) so you don't get quite so many results.

[EDIT] Just out of interest, what is the reason for compiling gdesklets?  (I'm not suggesting you shouldn't it's entirely your choice) is it not in the repositories?
[EDIT AGAIN] Nevermind, it's the latest version you are installing so I guess that's why.

---

### Post by dunomous on 2006-03-28
Hooray! Success! Thank you so much sir.

well, except for this python mess.

```

configure: error: Can't find Python.h! You will need the python development package
              to successfully compile gDesklets.

```

---

### Post by fannymites on 2006-03-28
No so sure about that one.  Try searching through synaptic and see what version of python you have installed then install the python-dev package with the same version number.

---

### Post by dunomous on 2006-03-28
Yeah, was just doin that, I have 2.4, apparently the latest listed, installed. Obviously, while perusing through what's installed with it, not everything is chosen. I'm not sure as to what it needs for it to work, I'd like to not install all of it if I don't have to. any ideas?

-edit-

Oh, and this could help.
```

checking /usr/include/python2.4/Python.h usability... no
checking /usr/include/python2.4/Python.h presence... no
checking for /usr/include/python2.4/Python.h... no

```

---

### Post by fannymites on 2006-03-29
I did a quick google search and Python.h is definately in the python-dev package so try apt-get install python-dev or apt-get install python2.4-dev

---

### Post by dunomous on 2006-03-29
So I installed the python-dev package and received this: 

```

checking for GDESKLETS... configure: error: Package requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GDESKLETS_CFLAGS and GDESKLETS_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```

Perhaps just a simple reboot will solve the problem?

---

