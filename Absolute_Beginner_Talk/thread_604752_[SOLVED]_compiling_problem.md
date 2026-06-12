---
title: "[SOLVED] compiling problem"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by neoragexxx on 2007-11-06
hi people :)

 my problem is that the libraries i want to use for the source i want to compile are in another directory .

for example pcctscfg.h is in /usr/include
but i am compiling from /blabla/Desktop/test. 

so it doesn't find it. what do i need to do to make it find my libraries in other directories also when compiling ? 

it tried PATH=$PATH:/usr/include 
but didn't work :( 

any help would be greatly appreciated

thanks in advance

---

### Post by twiceasworn on 2007-11-06
> **neoragexxx said:**
> hi people :)

 my problem is that the libraries i want to use for the source i want to compile are in another directory .

for example pcctscfg.h is in /usr/include
but i am compiling from /blabla/Desktop/test. 

so it doesn't find it. what do i need to do to make it find my libraries in other directories also when compiling ? 

it tried PATH=$PATH:/usr/include 
but didn't work :( 

any help would be greatly appreciated

thanks in advance

After you specify what the path is, you must export the path to your bash settings. You can do this by doing:

```

export PATH=Whatever

```

You could alternatively hardcode the path into your bash settings by editing the .bashrc in your home directory and adding the export in there.  Then it would do it for you every time you log in.

---

### Post by Arthur Archnix on 2007-11-06
I don't know much about compiling, but it sounds like you want to try a symlink. From another [thread]("http://ubuntuforums.org/showthread.php?t=255573"):
```
ln -s /path/to/real/file /path/to/non-existant/file
```

If you look at [this]("http://www.howtoforge.com/kernel_compilation_ubuntu") document on kernel compilation in ubuntu you'll note they use symlinks a bit.

---

### Post by Adramelech on 2007-11-06
use pkg-config, it returns the libraries you need for compile for certain package

example:

$ pkg-config --libs pango
-lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  

gcc  `pkg-config --libs pango` mysource

---

### Post by neoragexxx on 2007-11-08
thanks guys ,  i tried the symlink succesfully but then i discovered that my newly installed ubuntu does not have basic c libraries like stdio.h and stdlib.h :S 

how do i install the c libraries ? i don't know the name or how to find them in the synaptic package manager..

---

### Post by kevdog on 2007-11-08
sudo aptitude install build-essential linux-headers-`uname -r`

---

### Post by neoragexxx on 2007-11-08
hey man thanks it worked like a charm . I was just wondering why aren't these automatically installed by the dvd installation . cause the way i see it no linux beginner could figure that command out without asking :)

---

