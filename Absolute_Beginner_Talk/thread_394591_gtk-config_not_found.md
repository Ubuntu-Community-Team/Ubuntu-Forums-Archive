---
title: "gtk-config not found"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-27
I've been trying to install an Epson 3170 scanner and am having trouble getting the software to recognize the device. I've tried a variety of things (see following thread) with no success.

[http://www.ubuntuforums.org/showthread.php?t=393882](http://www.ubuntuforums.org/showthread.php?t=393882)

Is there some way to get this scanner to work?

---

### Post by lloyd_b on 2007-03-27
I know nothing about scanners.  But I can provide this information: "gtk-config" is a part of the package "libgtk1.2-dev".  

Hope this will help...

Lloyd B.

---

### Post by lwalper on 2007-03-27
OK. Thanks. Got that one. Now it tells me it can't find the package 'imlibgdk'.

I've looked in synaptic which does not seem to be able to find it??

---

### Post by lloyd_b on 2007-03-27
> OK. Thanks. Got that one. Now it tells me it can't find the package 'imlibgdk'.

I've looked in synaptic which does not seem to be able to find it??

Try these two: "gdk-imlib11" and "gdk-imlib11-dev".  I'm not sure that these are the correct packages - they're just the only ones I see that look reasonable for "imlibgdk"

Lloyd B.

---

### Post by lwalper on 2007-03-28
I was reading another forum

[http://forum.freespire.org/showthread.php?p=45532](http://forum.freespire.org/showthread.php?p=45532)

Could it be that the file I'm looking for has been decremented? Seems like some else should have run across this some time recently, but I'm not finding a lot of question about it.

I've installed more libraries -- still "No device found"

---

