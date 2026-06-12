---
title: "Dual-Boot mac os x kernel panic"
date: 2007-02-27
forum: Apple PPC Users
---

### Post by robTard on 2007-02-27
Hi, I have a problem.

I have ubuntu edgy eft and mac os x on different partitions.
Recently I've been fooling around with /etc/yaboot.conf because my machine was booting into mac os x automatically.
Anyways, now when I try to boot into mac os x, it kernel panics.  here is what my /etc/yaboot.conf looks like: 

boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=7
root=/dev/hda7
timeout=30
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        initrd-size=8192

macosx=/dev/hda5
enableofboot

Also, for some reason, when I open up gparted, I can't see any of the partitions that I used to be able to see: /dev/hda through /dev/hda9
I *may have* deleted the APM (Apple Parition Map), does anyone have any solutions?
Thanks, Rob

---

### Post by pxwpxw on 2007-02-28
This might help, note that the partition numbers are different,
the key point is 
```

###
### next 2 lines I added to make first stage boot menu default to maacosx (x)
### requires run ybin again. see man yaboot.conf, ybin.
macosx=hd:3
defaultos=macosx
###

```


You have to give it the Open Firmware path for macosx hd:3 here
(equivlent to /dev/hda3)
And you have to run ybin.

[COLOR="DarkOrange"]Link to thread, see my post in page 2, near the end.
[/COLOR]
[COLOR="DarkOrange"][http://ubuntuforums.org/showthread.php?t=357022&page=2](http://ubuntuforums.org/showthread.php?t=357022&page=2)
[/COLOR]
Also if you can still boot linux I doubt you have zapped the partition map.

Try 
```

sudo mac-fdisk -l

```

---

### Post by robTard on 2007-03-01
After running sudo mac-fdisk -l it looks like I didn't zap the partition map b/c
the command prints all my partitions with names.

Thanks for the help, I'm going to edit my yaboot.conf later and see what happens.

---

