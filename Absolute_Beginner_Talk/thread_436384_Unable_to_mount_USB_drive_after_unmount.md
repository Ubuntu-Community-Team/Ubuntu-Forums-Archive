---
title: "Unable to mount USB drive after unmount"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by REMcCain on 2007-05-07
Hi,

I have a small problem and I have searched through and tried some of the advice in this forum. 
I have 2 externally mounted USB hard drives (80gb each, I think) named alpha and beta.
at least, I call them by those names...

So, about 20 min ago, I decided to unmount beta and mount alpha.
I normally just turn the drive off, unplug, swap and turn the new one on.
but this time I unmounted before I did any of that.

No big deal, I thought.

I swapped everything around and waited for Ubuntu to read the drive... and waited, and waited... no luck.  I could see all the flash drives that activate when the USB-HD  is active, so I know it has power.  I know, well, I'm reasonably certain, that the HD unit is still good.  I was using it just a few days ago.

So I did this;
$ sudo fdisk -l

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hda2            6375       12748    51199155   83  Linux
/dev/hda3           12877       38913   209142202+   b  W95 FAT32
/dev/hda4           12749       12876     1028160   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sde: 81.9 GB, 81961122816 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        9964    80035798+   7  HPFS/NTFS

and I can see the darn thing at dev/sde1

so then I try;
$ sudo mount -t ntfs /dev/sde1 /mnt/sde1
mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


So what am I doing wrong?
Thanks :)

---

### Post by Tundro Walker on 2007-05-07
Not sure what's wrong, but you can dump out an error log for the mounting command you're using by doing this...

```
sudo mount -t ntfs /dev/sde1 /mnt/sde1 > /home/HelloKitty/Desktop/t.log 2>&1
```

Replace the word "HelloKitty" with whatever your home directory is.  This will basically dump out the results, both good and bad, from the command run into a log file called "t.log" onto your Desktop.

You can then open the log file, and copy/paste the results into a reply on here.  That should help folks out if they're trouble-shooting your issue.

---

### Post by REMcCain on 2007-05-07
> **Tundro Walker said:**
> Not sure what's wrong, but you can dump out an error log for the mounting command you're using by doing this...

```
sudo mount -t ntfs /dev/sde1 /mnt/sde1 > /home/HelloKitty/Desktop/t.log 2>&1
```

Replace the word "HelloKitty" with whatever your home directory is.  This will basically dump out the results, both good and bad, from the command run into a log file called "t.log" onto your Desktop.

You can then open the log file, and copy/paste the results into a reply on here.  That should help folks out if they're trouble-shooting your issue.

Here's the log file:

t.log
mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

end log

In other news, I swapped Alpha out for Beta and Beta is now working.  I think maybe Alpha has issues unrelated to Ubuntu.

Thanks for the help.

---

