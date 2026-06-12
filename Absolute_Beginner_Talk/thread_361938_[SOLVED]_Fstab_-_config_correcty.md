---
title: "[SOLVED] Fstab - config correcty"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by uclalinux on 2007-02-15
I know a little about linux but am haveing problems booting. I belive that it might be corrasponding to my fstab mount. I am running ubuntu as a samba and apache server and i have a extra hard drive mounted. I install xubuntu correctly and have config it. now as of last night everything was working properly. but this morening not was working. I cant even boot. once the grub load begins the computer works VERY slowy.  I mean very slowy. I am at a lost. I have run ubuntu on this system befor and it was fine. If you want to know why i am using xubuntu instead of ubuntu server its becuase ucla is F!*#K dumb and i have to do alot of regersting over a gui. Please help if any ideas

Hardwear: 
PIII 866, 512 Mb Ram, 64 MB video, some AZZA 693btx mother board. 4.3 Gb HD which has on one partison the root and sawp, on another partion it has the /boot, and then a second hard drive with all the music and samba files on it.

---

### Post by sardion on 2007-02-15
Hard to tell from what you said.  If you think its fstab, post the file.

My guesses: the / partition is full ? (if something fails to mount and then stuff gets copied to what it should be mounted it often fills the disk)  or hate to say it but maybe your drive or IDE is dying?  Post fstab and if possible anything relevant from syslog.


p.s. i'm also ucla and last year i managed to avoid their gui registering thing by doing IP spoofing ... I used my laptop (which has X11) and set it up to spoof my server's mac address... did the registration, then conencted the server and it worked fine.. .disabled spoofing on lapttop and everything was cool.  but that was a year ago.

---

### Post by uclalinux on 2007-02-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda1
UUID=06914f1a-d729-4ebc-9c18-a2d080d548b1 /boot           ext2    defaults        1      2
/dev/hda3
UUID=42002ec9-68a9-43a1-b88f-291e70c7c33e /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2
UUID=80963f1d-e26c-4b81-b9cb-b592913fa520 none            swap    sw              0       1
/dev/hdb1	/home/matt/musicserver       ext3      defaults     0      1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
proc            /proc           proc    defaults        0       0



I think proc needs to be at the top, but i dont get what is all the "UUID=80...." junk,

---

### Post by sardion on 2007-02-15
You can try moving proc to the top but that shouldn't matter.

The UUID stuf fis ubuntu's new way of labelling disks, it is designed so that removable disks can be mounted to the same place no matter what they show up as ... so like a usb drive may be /dev/sda or /dev/sdb etc but if it is referred to by UUID then it will always mount in the same place.  In short, it doesn't affect your setup.

You sure your disk isn't full?

You might want to run a disk test and memtest.

---

### Post by igknighted on 2007-02-15
Sounds more like a grub issue... what's your /boot/grub/menu.lst file?

---

### Post by Patrick K on 2007-02-15
If you are interested in what devices have what UUID, fire up Device Manager and find the device you are interested in. Click on it then the advanced tab. At the bottom of the list is the UUID number.

---

### Post by uclalinux on 2007-02-15
i cant find the /boot/grub/menu.lst

---

### Post by Patrick K on 2007-02-16
What do you find when you look in /boot/grub?

Try this in a terminal (application>accessories). Just copy and paste this command. > gksudo gedit /boot/grub/menu.lst

---

### Post by mcduck on 2007-02-16
There are some strange things in your fstab indeed. They might or might not be the cause of you problem, but you could try this one instead:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda1
UUID=06914f1a-d729-4ebc-9c18-a2d080d548b1 /boot           ext2    defaults        0      2
/dev/hda3
UUID=42002ec9-68a9-43a1-b88f-291e70c7c33e /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2
UUID=80963f1d-e26c-4b81-b9cb-b592913fa520 none            swap    sw              0       0
/dev/hdb1	/home/matt/musicserver       ext3      defaults     0      2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
proc            /proc           proc    defaults        0       0
```


For one thing, you had fsck on swap partition enabled, which makes no sense. Then only / should have a '1' as the last number in the entry, for other partitions you should use either '2' (to run fsck after /) or '0' (to not check the partition).

I'm not sure about the dump that you had configured for /boot though.

---

### Post by uclalinux on 2007-02-26
thanks got it working

---

