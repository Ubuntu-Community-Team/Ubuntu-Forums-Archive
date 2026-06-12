---
title: "Help with C compiler"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by LoneGalleon on 2006-07-18
I was trying to install xmms by following the basic installation instructions in the given readme. I was doing fine until I got up to typing in "./configure". The terminal returned a few system checks as well as "configure: error: no acceptable C compiler found in $path"

Correct me if I'm wrong, but isn't ubuntu supposed to come with a C compiler? So how would I go about approaching this problem?

---

### Post by taurus on 2006-07-18
Open a terminal and type

```

sudo apt-get update
sudo apt-get install build-essential

```

---

### Post by xXx 0wn3d xXx on 2006-07-18
> **LoneGalleon said:**
> I was trying to install xmms by following the basic installation instructions in the given readme. I was doing fine until I got up to typing in "./configure". The terminal returned a few system checks as well as "configure: error: no acceptable C compiler found in $path"

Correct me if I'm wrong, but isn't ubuntu supposed to come with a C compiler? So how would I go about approaching this problem?
Try:
> sudo apt-get install build-essential
or:
> sudo apt-get install gcc

then while before compiling, run this:
> sudo apt-get build-dep xmms

Note: this will only work with applications in the repositories

---

### Post by rivera82falcon on 2006-07-27
I performed these and it updated like it should...now, I tried compiling and in the end, I get this message:

The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.

How do I install this?

---

### Post by IYY on 2006-07-27
Just a question... Why are you compiling XMMS? It's in the repositories, you know. All you need to do to install it is

```
sudo apt-get install xmms
```

---

### Post by rivera82falcon on 2006-07-28
Aaah!!! Okay, thanks! I'm very new to linux/Ubuntu and I still have a LOT to learn. Thanks though.:D

---

### Post by OU812 on 2006-07-28
When installing from source, should we do

```
./configure
```

or

```
./configure -prefix=/usr
```

Thanks.

john

---

### Post by rivera82falcon on 2006-07-31
But how would I install GLIB? I mainly wanna know this for systems that do NOT have an internet connection (no access to apt-get). 

I already have GLIB downloaded...how do I install it? 

I used the apt-get command to install XMMS..thanks =) Just wanna obtain more knowledge about Ubuntu and Linux.

---

### Post by Bloch on 2006-07-31
The days when linux users were expected to compile their software are long gone. Most of my attempts to compile have failed miserably and I think a lot of sites that say "download this and enter ./configure . . . " should carry a warning: "This is for power users only."
All good software is available pre-compiled.

Having said that, more power to you if you've decided to go down that road. 

> I already have GLIB downloaded...how do I install it?
Is it a .deb file? Then double-click on it. If it isn't then don't install it. It might break your system. 
Use synaptic. The only things not available through synaptic are google-earth and picasa.
 
 Here's a good guide:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by rivera82falcon on 2006-07-31
> **Bloch said:**
> The days when linux users were expected to compile their software are long gone. Most of my attempts to compile have failed miserably and I think a lot of sites that say "download this and enter ./configure . . . " should carry a warning: "This is for power users only."
All good software is available pre-compiled.

Having said that, more power to you if you've decided to go down that road. 


Is it a .deb file? Then double-click on it. If it isn't then don't install it. It might break your system. 
Use synaptic. The only things not available through synaptic are google-earth and picasa.
 
 Here's a good guide:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Awesome! Thank you VERY much! This had exactly what I needed and more! I appreciate your help...everyone!!!

---

