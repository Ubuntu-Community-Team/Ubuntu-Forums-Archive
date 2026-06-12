---
title: "how to move partitions off desktop"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by jiminid on 2007-05-03
Hi,
Have a clean install of unbuntu 7.04 but when it boots up, I have all of my partitions showing up on my desktop. Can I delete these without breaking anything? already available in /home/mnt right? Only need hda1 (windows) oh yeah now its sda1 (why is that?) if my ide is sda1 what is a sata or scsi drive? Anyway, all I want on my desktop is sda1, sdb14, sdb16, sdb17, cdrom, dvd, floppy/media reader. right now I have sda1 thru sdb18. All help would be appreciated. But, so far, it just works!

jiminid

---

### Post by gerscht on 2007-05-03
comment out the corresponding entries in /etc/fstab 
```
sudo gedit /etc/fstab
```
This will prevent the drives from being auto mounted.

---

### Post by mikewhatever on 2007-05-03
If you do that, these partitions will not be mounted.

---

### Post by jiminid on 2007-05-04
Thanks for the help.
I think I don't mind that they automount. In fact, I think that's pretty cool. Would like to create one folder on the desktop titled...Partitions. put all the hard drive partitions in there. create the folder and drag and drop them? Can I rename them without breakage?

thanks for your help.

jiminid

:confused:

---

