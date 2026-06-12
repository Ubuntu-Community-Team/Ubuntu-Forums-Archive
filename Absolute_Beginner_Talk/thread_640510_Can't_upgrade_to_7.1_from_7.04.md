---
title: "Can't upgrade to 7.1 from 7.04"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by ansextra on 2007-12-14
I was just notified that 7.1 has been released.  I tried to do the automatic upgrade from 7.04 but was informed that I needed more disk space.  I need to change the partition space that I have allocated for Ubuntu.  
My original 7.04 CD isn't working so I downloaded 7.10 but it doesn't give me an "upgrade" or "partition" option?
How can I increase the size of the partition and then upgrade Ubuntu?

I'm pretty good at Windows but trying to learn Linux... ;)

---

### Post by vanadium on 2007-12-14
You can repartition your disk using gparted. There is a dedicated gparted live CD that you can download and which seems to be excellent, but I have no experience with it. You can also use the Ubuntu Live CD (7.04 or 7.10, should not matter). Once in the live session, open a command prompt and load gparted by typing "sudo gparted". Then you can change the partitioning of your disk. The details of how to proceed best depend very much on your specific configuration.

Before attempting any of this, make sure all your personal data are backed up. There is always a chance that something goes wrong to the extent that you loose your data.

---

### Post by perfecttao on 2007-12-14
You can use the livecd and then use gparted to increase the partition size.

[http://ubuntuforums.org/showthread.php?t=115344](http://ubuntuforums.org/showthread.php?t=115344)

As a recommended long term solution, I would recommend moving your /home drive to a separate partition and then do a full reinstall of the whole OS (this will then allow you to reinstall without risking losing data).

Every time I've tried to do an upgrade it's always been "buggy" whereas reinstalling everything seems to work smoothly!

---

