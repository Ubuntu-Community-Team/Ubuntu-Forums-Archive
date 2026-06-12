---
title: "mounting a 2nd hard drive in Fluxbuntu"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by rockerphil on 2008-04-04
ok, i have been using Fluxbuntu for a while on my old Dell Dimension desktop and am enjoying it. my problem is this, i've got 2 hard drives on my machine, the original, and a 2nd one that a friend gave me for storage when the machine was still running Windblows that i just can't seem to get mounted in to my file system. i'd reformat the 2nd hard drive to a Linux partition, but i have a lot of music (which is no big deal losing) but i've also got quite a bit of family pictures on it, and since this machine doesn't have a CD burner i was unable to back the media up. my GRUB boot loader detects the Windows XP install on the secondary drive but i don't have the system specs to boot in to it and save my pictures. any type of help would be appreciated. thanks

---

### Post by aeiah on 2008-04-04
you should be able to temporarily mount it from the command line. all devices are stored in /dev/. your main hard drive partition is probably /dev/hda and your second one is probably /dev/hdb, although this might not be the case.

to temporarily mount it, use the terminal and find out what your drives are called. type:

```
ls /dev/h*
```

this'll list everything that begins with 'h' thats in there. you should be able to figure out which one is your 2nd hdd.

make the directory to mount it to:
```
sudo mkdir /media/storage
```

and mount the device:
```
sudo mount /dev/hdb /media/storage
```

if you're going to wipe it after moving important files, you dont need to bother mounting it permanently just yet, but if you do, you can add it to your fstab file. there should be plenty of posts on here that talk about fstab. its where linux looks to see where to mount all your partitions and such at boot time

---

