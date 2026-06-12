---
title: "Xgl? =)"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by Neuros on 2006-06-18
Which XGL package do i download? Is there a guide for installation in Ubuntu Dapper Drake?

I went to a mirror, and there where so many XGL/Compiz packages; I didnt know which one to get. I have used linux since th release of Red Hat =P

---

### Post by Anduu on 2006-06-18
Which video card are you using?

---

### Post by hegenious on 2006-06-18
try to find a script that does it neatly for you
there was a post about that, on this forum, that worked for both ati and nvidia. [http://www.ubuntuforums.org/showthread.php?t=147049](http://www.ubuntuforums.org/showthread.php?t=147049)
but apparantly it has been deprecated.

it downloaded and installed a few packages (Xgl and compiz) and edited five config files. An important prereq is to have the proprietary driver for your hw installed.
In my case it is the fglrx driver. make sure the section in xorg.conf says "fglrx" and *not* ati 'cause then it won't work

with this inst_xgl.sh script I was up & running with all the eyecandy enabled and a config interface in about ten minutes. I can pm you the script if you want, but no guarantee that the weblinks in the script still work.

I must say that before I stumbled upon the above script, all my temptatives to install Xgl/compiz failed miserably  :P

ps: you will find all the files here: [http://www.futuredesktop.org/dapper/](http://www.futuredesktop.org/dapper/)  note that the script has been renamed to .OLD

---

### Post by TristanMike on 2006-06-18
Personally I used the [Wiki](https://wiki.ubuntu.com/CompositeManager) and on my hardware (shown below) it was flawless. It keeps me updated and it's running very well, I personally recommend it.

TM

---

