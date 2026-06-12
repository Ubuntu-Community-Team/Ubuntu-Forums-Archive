---
title: "Where to put a program - dumb question"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by gantww on 2006-09-04
Ok,
I managed to get Ubunutu installed and configured, along with MySQL and everything else I needed/wanted. I found a great program for setting up Ruby on Rails based websites. However, when I downloaded it, it came in a tarball. Upon extracting the files, I had a directory for a working program. That's great and all, but I would like the following.
1) To put it in a more appropriate location in my filesystem
2) Make it available to other users on the machine.
3) Make it accessible from the startup menu
4) Make sure it plays nice with the paths of everything else on the system.

How do I do this?

---

### Post by maelgwynffn on 2006-09-04
So it did not have a Makefile?  Normally, if something is tarballed, it can be installed.  But if you want to put it somewhere, I would put it in your home directory.

But I think you *normally* would have to use 'make install'

Err... that probably doesnt help.

Mael

---

### Post by gantww on 2006-09-04
That's what I was thinking. There isn't a makefile in there at all. It's a variant of Eclipse (I'm guessing, anyway). It's called RadRails and is downloadable from RadRails.org. I think maybe the deal is that it is still in a pre-1.0 status (beta or otherwise).

Where exactly in the file system are programs (like IDEs) typically stored? Is there something similar to Program Files in Windows?

---

### Post by maelgwynffn on 2006-09-04
--------------------------------------------------------------------------------

...thought it might be useful to peeps

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Found something I needed to know on it, and the rest was good.


~~~~~~~~~~~~~~~~~~~~

This is from another post about installing stuff

[http://www.ubuntuforums.org/showthread.php?t=250839](http://www.ubuntuforums.org/showthread.php?t=250839)

I found that is is applicable here

Have fun

Mael

---

### Post by maelgwynffn on 2006-09-04
/usr/bin

/bin

/usr/sbin

Or wherever you want!  That is the beauty of Linux (it took me ages to get my head around this)

Mael

---

### Post by maelgwynffn on 2006-09-04
I really should think before I make 20 posts

Installation Instructions
Make sure you have Ruby installed (1.8.4) 
Make sure you have the Rails framework installed (1.1) 
Make sure you have Java 1.4+ installed 
Download the zip for your platform 
Extract the zip 
Run the "radrails" executable 
Video

---

