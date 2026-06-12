---
title: "Boot Issue"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by meney on 2007-03-03
Hey everyone,

I have been having a problem with boot sequence since I started using Ubuntu. I have been too lazy to post a topic about it until now, as it is not detrimental to the workings of my machine. ;)

Anyway, I'm running a dual boot of windows XP and Ubuntu, but whenever I startup Ubuntu it seems to do a file systems check every boot. I assume that this is the case, but I'm not sure how to determine this, or how to set the system to stop doing these checks (or once every 5 boots perhaps?). The reason being is that it takes so much more time to boot than if it did not preform this check.

PS: I hate to say this, but yes, Windows does boot faster ](*,)

---

### Post by Amenemhet on 2007-03-03
You can change that setting, although I don't know why it is running fsck at every boot. The file to change in fedora is the /etc/fstab, but I am not 100% sure it is the same file in Ubuntu. (sorry can't check mine at the moment or I would for you) Look in /etc/ directory for a file called fstab, if it is there, I believe it is the last entry on the right. (you will see your device name, then the mount point, then the file system type, then the mount options, then dump and last is the fsck) If you set the last entry to zero, the boot loader will not run fsck at boot.

Alternatively, you can man tune2fs. This is a utility to change settings, and I think the option is ...
tune2fs -c (#of boots till fsck will run, ie:33=every 33 boots) /dev/device
-c or -C, man tune2fs to be sure, I think I set mine a while ago to this..
tune2fs -c 33 /dev/hda5
Double check the man pages to be sure.

---

### Post by meney on 2007-03-04
Okay, I did all that but my boot time still seems to be really slow :(
I have added a boot chart, could someone take a look and see if their are any problems, or anything I can do to make my system boot faster?

Thanks In advance everyone! :KS

---

### Post by meney on 2007-03-04
Hum... I think I may have solved it, I set my windows drive to 0 in that file, and my documents drive to 2 under the pass option (although I'm not sure what the 2 option does... but the help file says only the root drive should be set to 1, Hurm...). Well it seems to boot faster now anyways :D

Thanks Everyone!

---

