---
title: "Still grinding..."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by RogerDavis on 2007-04-21
Upgrading from 6.10 -> 7.04 

I keep getting the same error (failed to fetch XXX, Sub-process bzip2 returned an error code (2)), about a dozen files named, check network and try again, and again, and again... now about 50 times or so.

One time it got all but about 6, but the next time it didn't find those, and back to about a dozen missing!

I'm using the update manager, I'm not up to the "renaming" method, and besides I've seen dire warnings about don't do it.

Is there a way to download a file or CD and upgrade from that, instead of depending on real time downloading? I'd rather keep my current setup than fight my way back to what I have done now. The upgrade to 6.10 kept it ok...

I'm told in answer to the above "Download the "Alternate" Cd", but that seems just for machines with very little memory.   Or maybe just wait a few days or weeks until the server use drops, assuming that is the problem?

Like the title says, Absolute Beginner... so :
1) How do I put it in Synaptic as a CD Repository?  Do I have to burn a CD, or can I just use a hard disk file, or is that what this means?
2) Afterward, how do I remove from the list?
Thanks!

---

### Post by slickidiotfan on 2007-04-21
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Hope that helps.

---

### Post by RogerDavis on 2007-04-21
Been there, done that, about 50 times now (NOT an underestimate!)
Thanks anyway...  Any other ideas?

---

### Post by slickidiotfan on 2007-04-21
Try in the terminal:

```
sudo aptitude install ubuntu-desktop
```

I wouldn't know what happens because mine is already upgraded, say if anything works with that.

---

### Post by RogerDavis on 2007-04-22
Got this result:
=======================
roger@roger-desktop:~$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
roger@roger-desktop:~$ 
=============================
Was this to run a disk to install?

---

### Post by slickidiotfan on 2007-04-22
```
sudo apt-get dist-upgrade
```

I'm starting to run out of ideas before we have to get technical.

---

