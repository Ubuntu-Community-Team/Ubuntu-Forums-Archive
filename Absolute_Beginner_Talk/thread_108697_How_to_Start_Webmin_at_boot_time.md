---
title: "How to Start Webmin at boot time?"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by beagle on 2005-12-26
So far,
I have installed Webmin-1.250 (tar.gz) in etc/webmin as a root user.
The webmin directory has root access.
If I manually start Webmin (by /etc/webmin/start), I am able to access webmin from my browser. 
How do I make webmin's server (or whatever) automatically launch when I boot my computer?   Thanks.

---

### Post by odin on 2005-12-27
try using the boot up manager

sudo apt-get install bum

it's a very good tool to choose what you want to run at boot time.

---

### Post by beagle on 2005-12-27
[QUOTE=odin]try using the boot up manager

sudo apt-get install bum

it's a very good tool to choose what you want to run at boot time.[/QUOTE]

Installed Boot-up manager.
Bum doesn't see Webmin :(

---

### Post by odin on 2005-12-28
Well that's a bit of a problem but try this thread that may help you

[http://ubuntuforums.org/showthread.php?t=93966](http://ubuntuforums.org/showthread.php?t=93966)

---

### Post by beagle on 2005-12-28
[QUOTE=odin]Well that's a bit of a problem but try this thread that may help you

[http://ubuntuforums.org/showthread.php?t=93966](http://ubuntuforums.org/showthread.php?t=93966)[/QUOTE]

Before your reply arrived, I had removed the current webmin (v1.250) and installed a 'webmin.deb-1.3' package using Synaptic.  Now, every thing is ok.
Thanks very much for the help; I am sure it will help me during future installations of non-deb distros. :D

---

