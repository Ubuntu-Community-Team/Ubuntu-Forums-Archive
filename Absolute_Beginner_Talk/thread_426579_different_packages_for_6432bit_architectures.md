---
title: "different packages for 64/32bit architectures?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by no.t on 2007-04-28
I was searching for package "mknbi". It seems to be in Synaptic for i386 systems, but missing for my amd64 box with Ubuntu 7.04/64bit.  
I want to make a kernel for diskless pxe booting. Maybe diskless systems will be mixed 32/64bit boxes. Should I use i386 kernel for both types? How can I make an i386 kernel on my 64bit box? 
(I got an error "Error invalid architecture i386" when installing "mknbi-1.4.4,orig.tar.gz" package on my amd64 box)

---

### Post by Happy_Man on 2007-04-28
Yeah, there are a lot of packages missing in the 64bit repos, because people are generally too lazy to make a 64bit package :( I'm not sure if you can compile a 32bit kernel on a 64bit system, though I don't see why you couldn't. Don't take my advice though, I've never really been one for compiling (.debs ftw!) :D Hope this helps!

---

### Post by zvacet on 2007-04-29
[http://sourceforge.net/project/showfiles.php?group_id=4233&package_id=11856]("http://sourceforge.net/project/showfiles.php?group_id=4233&package_id=11856")

Download tar.gz file and compile it.

---

