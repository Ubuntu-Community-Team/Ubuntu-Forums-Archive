---
title: "GRUB misconfiguration on dapper install"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by roger99 on 2006-09-14
I'm after some advice.......

I have two hard disks a IDE drive and a SATA drive.  Windows is installed on the SATA and I have put ubuntu on the IDE.  When grub installed (on hda) it picked up on windows and attempted to place an option to boot from it.  It doesn't work!!.  It appears to have mapped the drives wrong from what I can tell.

Here is the output from fdisk.

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            9555       30400   167445495    f  W95 Ext'd (LBA)
/dev/sda3            3188        9554    51142927+   7  HPFS/NTFS
/dev/sda5            9555       10319     6144831    7  HPFS/NTFS
/dev/sda6           10320       17974    61488756    7  HPFS/NTFS
/dev/sda7           17975       21799    30724281    b  W95 FAT32
/dev/sda8           21800       30400    69087501    7  HPFS/NTFS

and here is the segment of menu.lst referencing the windows installation

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

Do I change the hd1's to 2's or to sd's i'm not really sure.

Any advice would be great...  Cheers.

---

### Post by bodhi.zazen on 2006-09-14
try adding a single line "boot" (without quotes) on the line after "chainloader +1" & re-boot.

---

### Post by roger99 on 2006-09-14
Cheers I'll give it a go

---

### Post by roger99 on 2006-09-14
It still doesn't work, I get.....

root (hd1,0)

Error 21: Selected Disk does not exist.

and then it drops back to grub.

---

### Post by bodhi.zazen on 2006-09-14
Comment out the two map lines.

# map (hd0) (hd1)
# map (hd1) (hd0)

---

### Post by roger99 on 2006-09-14
Nope, i'm still gettin the same error.

---

### Post by xhaan on 2006-09-14
Edit: I didn't notice the error 21 part, so what I posted may not fix the problem. I tried googling for an answer but couldn't find one that was satisfactory... it seems a few people have problems with SATA drives though.

You'll need the map lines if Windows is on the second drive.
Instead of
 ```
root (hd1,0)
```

Try this
 ```
rootnoverify (hd1,0)
```

I usually put my map commands above the rootnoverify, I'm not sure if it will make a difference but you can try it.

I did my own grub menu entry myself and it looks like this:
```
 title           Windows XP
map             (hd0) (hd1)
map             (hd1) (hd0)
rootnoverify    (hd1,0)
chainloader +1
makeactive
boot
```

It boots Windows from the second hard drive.

---

### Post by roger99 on 2006-09-15
That still hasn't worked.  Now I get the last few lines of menu.lst echo'd to the screen and the same error again.

root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

root (hd1,0)

Error 21: Selected Disk does not exist.

I don't think it should make much difference but the SATA is connected through a PCI interface card rather than being native to the motherboard.

---

### Post by Najand on 2006-09-15
Shouldn't it to be like this?
```

title Microsoft Windows XP Professional
root (sd1,0)
savedefault
makeactive
map (sd0) (sd1)
map (sd1) (sd0)
chainloader +1

```

---

### Post by roger99 on 2006-09-15
Thats what I had assumed before my first post but didn't want to mess around with the file to much without some reassurance.  I'll give it a go and let you know.

---

### Post by Najand on 2006-09-15
Sure, I am waiting for your reply.

---

### Post by roger99 on 2006-09-15
Unfortunatly that still hasn't worked.  Now I get.....

root (sd1,0)

Error 23: Error while parsing number

---

### Post by Najand on 2006-09-15
As far as it it the first partition of yoour drive, it might be:
```

title Microsoft Windows XP Professional
root (sd0,1)
savedefault
makeactive
map (sd0) (sd1)
map (sd1) (sd0)
chainloader +1

```
Can you  give it a try?

---

### Post by roger99 on 2006-09-15
I've tried that Najand and it's still giving me an error 23.

---

### Post by Najand on 2006-09-15
```
title Microsoft Windows XP Professional
root (sd0,0)
savedefault
makeactive
chainloader +1
```
Can you  try this one and check it out again... I am sorry it is getting long but I hope it works this time.

---

### Post by roger99 on 2006-09-15
No need to apologise, your time and help is appreciated.

I'll give it a go now.

---

### Post by roger99 on 2006-09-15
It's still giving me an error 23.  Baffling innit.  Can still boot the windows drive by selecting it in the bios as the first boot disk so theres no  problem there.  It would be handy to get it working through GRUB, although i'm not sure how much i'm going to use windows in the future anyway. MS Rubbish :lol:

---

### Post by Najand on 2006-09-15
Hmm, You can set the grub menu to change your default boot drive and itis not  really related to 1st or 2nd boot disk.

---

### Post by roger99 on 2006-09-15
Is that the relevane of the map commands.  Mapping either drive to where GRUB thinks it's got to read the MBR, or am I interpting them incorrectly.  Sorry, i've only been using linux for about a month, and i've still a lot to learn.

The reason i ask is what effect would this have

```
map (hd0) (sd0)
map (sd0) (hd0)
```

Or am i guessing with no idea of what i'm talking about :)

Durrrr.....   I've just spent the last hour reading about grub only to realise i'd inadvertingly disabled the hard disk as a boot device in BIOS.  It works now.  Sorry to have wasted peoples time.  I'll do more research before I post next time eh. #-o

---

