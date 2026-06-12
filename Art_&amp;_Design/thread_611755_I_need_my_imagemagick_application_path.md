---
title: "I need my imagemagick application path"
date: 2007-11-13
forum: Art &amp; Design
---

### Post by bjorntheart on 2007-11-13
Can anyone please help me find the path of my imagemagick installation.

I'm running ubuntu feisty

convert -version output, just to show it is installed
```
Version: ImageMagick 6.2.4 10/03/07 Q16 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2005 ImageMagick Studio LLC
```

---

### Post by Paul820 on 2007-11-13
If you go to the synaptic package manager and search for imagemagick, right click on the line where imagemagick is and select properties, click on the installed files tab and it will tell you where every file got put.

You can also type in the terminal
> **whereis name_of_program**

Replace name_of_program with the name of your program, :) obviously.

Hope this helps you out.
EDIT: ImageMagick is a collection of programs, not just one.

---

### Post by bjorntheart on 2007-11-14
Yeah Paul. 

Awesome. Thanx alot

---

### Post by opakedragon on 2007-11-15
When I try convert -version I get

```

The program 'convert' can be found in the following packages:
 * imagemagick
 * graphicsmagick-imagemagick-compat
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: convert: command not found
```

what do I do?

---

### Post by Paul820 on 2007-11-15
You need to install one of those programs to get the convert program. Either one has it.

---

### Post by opakedragon on 2007-11-15
I tried to but it said... *retries to get the output again*

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package imagemagick is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libmagick9
E: Package imagemagick has no installation candidate
```

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package graphicsmagick-imagemagick-compat
```

that.... how do I fix do I need to download one of them from a website? if so where do I get them?

---

### Post by Paul820 on 2007-11-15
image-magick is in the repos. Do you have all your sources checked in System->Administration->Software Sources?

---

### Post by bjorntheart on 2007-11-16
Found it.

It's in  /usr/bin/convert

That's the path

Thanx for all the help guys

---

### Post by opakedragon on 2007-11-16
thanks paul 820!!!

---

