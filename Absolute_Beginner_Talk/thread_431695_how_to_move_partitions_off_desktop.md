---
title: "how to move partitions off desktop"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by jiminid on 2007-05-03
Hi,
Have a clean install of unbuntu 7.04 but when it boots up, I have all of my partitions showing up on my desktop. Can I delete these without breaking anything?(yes, I know I get to keep both pieces but I have too many already...and they get stuck in the vacuum cleaner) already available in  /home/mnt  /home/user/mnt? right? Only need hda1 (windows) oh yeah now its sda1 (why is that?) if my ide is sda1 what is a sata or scsi drive? Anyway, all I want on my desktop is sda1, sdb14, sdb16, sdb17, cdrom, dvd, floppy/media reader.all mounted and ready to go, (how to separate floppy from media reader?) right now I have sda1 thru sdb18. All help would be appreciated. But, so far, it just works!

Thanks for your help!

jiminid

---

### Post by mikewhatever on 2007-05-03
Well, to remove all icons from the desktop, press Alt+F2 and type gconf-editor, then navigate to apps>nautilus>desktop, uncheck volumes visible.
If you want to keep some and remove the others, mount those you don't want somewhere other then in /media.

---

### Post by orb9220 on 2007-05-03
I created a Drives folder in /home and then created winXP folder and a Fat32 folder in Drives folder.

And then modified fstab to mount them there instead of /Media.
Anything mounted in /Media will show on desktop.

---

### Post by jiminid on 2007-05-07
> **orb9220 said:**
> I created a Drives folder in /home and then created winXP folder and a Fat32 folder in Drives folder.

And then modified fstab to mount them there instead of /Media.
Anything mounted in /Media will show on desktop.

Sounds good!

Thanks for the idea!

---

