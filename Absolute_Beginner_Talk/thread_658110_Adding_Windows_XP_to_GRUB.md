---
title: "Adding Windows XP to GRUB"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Cheesycrap on 2008-01-04
Hi guys, I have a grub problem.

Heres my current harddrive setup.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b1e87

Device Boot Start End Blocks Id System
/dev/sda1 * 1 8979 72123786 7 HPFS/NTFS
/dev/sda2 8980 19224 82292962+ 83 Linux
/dev/sda3 19225 19457 1871572+ 5 Extended
/dev/sda5 19225 19457 1871541 82 Linux swap / Solaris

/dev/sda1/ is the windows partition, which I need to create a boot option for, and the rest are all ubuntu bits and pieces.

My menu.lst looks like this,

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=fc0d9fe9-2c7e-41a5-88c8-ce90317e7751 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=fc0d9fe9-2c7e-41a5-88c8-ce90317e7751 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet


So going vaguely from a few forum posts, I came up with this for my windows xp option and when I rebooted to see if it would work, it got stuck at the "Starting up" dialog. So Im now back where I started in ubuntu.

Windows XP failure:

title WINDOEEEZ
root (hd0,0)
makeactive
chainloader +1

I Added this above the rest of the ubuntu sections, with spaces of lines in between. Where did I go wrong?

---

### Post by stump138 on 2008-01-04
First try to comment out your additions to /boot/grub/menu.lst and see if you simply made a syntax mistake.

---

### Post by meindian523 on 2008-01-04
Um,do you have a space between

root and (hd0,0) ?There should be.Plus add savedefault in the Windows entry above makeactive.

---

### Post by stump138 on 2008-01-04
You might also need to repair grub, [this ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")  is a good link for that

---

### Post by Cheesycrap on 2008-01-04
Ok, here is an exact copy of how my menu.lst looked after I added the windows xp bit in.

## ## End Default Options ##

title_____WINDOEEEZ
root____(hd0,0)
makeactive
chainloader +1

title______Ubuntu 7.10, kernel 2.6.22-14-generic
root________(hd0,1)
kernel_____/boot/vmlinuz-2.6.22-14-generic root=UUID=fc0d9fe9-2c7e-41a5-88c8-ce90317e7751 ro quiet splash
initrd/boot/initrd.img-2.6.22-14-generic
quiet

title_______Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root_______(hd0,1)
kernel______/boot/vmlinuz-2.6.22-14-generic root=UUID=fc0d9fe9-2c7e-41a5-88c8-ce90317e7751 ro single
initrd/boot/initrd.img-2.6.22-14-generic

title_______Ubuntu 7.10, memtest86+
root_______(hd0,1)
kernel______/boot/memtest86+.bin
quiet



And here is a copy of the section which I added in.


title______WINDOEEEZ
root______ (hd0,0)
makeactive
chainloader +1

I have now also added "savedefault" above makeactive as meindian has suggested and im about to do a restart to see if its done the trick.  Thanks for the quick reply's and sorry I didnt make the post very clear the first time.

UPDATE: It hasn't made the difference :(, still sticks at the "Starting up ..." dialog.  Replaced spaces with forced underline, auto formatting is really starting to annoy me. :@

---

### Post by Cheesycrap on 2008-01-04
Yeh so umm, I Dont really know what to do and I've got a LAN party in about an hour where i really need windows so anything really would help.

---

### Post by meindian523 on 2008-01-04
Please post cat /boot/grub/menu.lst and use the quote tags [ QUOTE ]...[ /QUOTE ] to avoid auto-formatting without the spaces between QUOTE and the square brackets "["

Also,you have to post the Windows entry at the END of the menu.lst.

---

### Post by dstew on 2008-01-04
The behavior suggests that grub is working OK, but Windows is not booting. Can you boot Windows in some other way, say using a Windows recovery console, or with a supergrub disk?

---

### Post by torgrot on 2008-01-04
Try using gag to boot of a floppy.  It has been a real lifesaver for me at times.  

torgrot

---

### Post by Cheesycrap on 2008-01-04
Back again.  I installed this windows xp partition on this harddrive but it was in the bootloader of another HDD which has killed itself.  Would that have anything to do with the problem?  Also heres menu.lst yet again.  Apparently Im a forum noob and a linux noob :P.

> 


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fc0d9fe9-2c7e-41a5-88c8-ce90317e7751 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fc0d9fe9-2c7e-41a5-88c8-ce90317e7751 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title           WINDOEEEZ
root            (hd0,0)
savedefault
makeactive
chainloader +1




Also no i cant boot windows any other way :(

---

### Post by dstew on 2008-01-04
> I installed this windows xp partition on this harddrive but it was in the bootloader of another HDD which has killed itselfDid you just copy the Windows XP to the new partition? If so, that might be the problem. In order for it to boot correctly, it has to be installed from a CD, just like Ubuntu. If you just copy it, and if the new drive has a different geometry, it will not boot properly.

---

### Post by klow717 on 2008-01-07
> **Cheesycrap said:**
> Hi guys, I have a grub problem.

Heres my current harddrive setup.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b1e87

Device Boot Start End Blocks Id System

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=fc0d9fe9-2c7e-41a5-88c8-ce90317e7751 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=fc0d9fe9-2c7e-41a5-88c8-ce90317e7751 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet


So going vaguely from a few forum posts, I came up with this for my windows xp option and when I rebooted to see if it would work, it got stuck at the "Starting up" dialog. So Im now back where I started in ubuntu.

Windows XP failure:

title WINDOEEEZ
root (hd0,0)
makeactive
chainloader +1

I Added this above the rest of the ubuntu sections, with spaces of lines in between. Where did I go wrong?
:):KS
I had an almost identical problem!
I wanted to use Ubuntu as dual boot with an existing WXP pro. all went fine when I had it installed with vers. 6.something. however when installed Vers.7.10 and restarted I noticed my WPX was no longer in the boot menu. 
Being an absolute novice with Ubuntu I found this excellent forum and learned about using the terminal program to get into the grub editor with(thank you so very much stump 138 for your most helpful link) "gksu geedit /boot/grub/menu.lst  (it is a"l" not a "1")
I followed all the advice and edited at the end the following in:
Title        Windows XP pro
root        (hd0,0)
makeactive
chainloader +1

Just as the other post I had no luck.
I than decided to add  /dev/sda1 (the actual partition my WXP was installed on the hard disk) behind the 'root (hd0,0)'!
So now it read:
Title       Windows XP pro
root       (hd0,0)  /dev/sda1
makeactive
chainloader +1

It worked!!!
Again thank you all for your help! :)

---

