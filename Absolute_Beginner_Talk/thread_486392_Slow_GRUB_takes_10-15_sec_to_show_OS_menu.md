---
title: "Slow GRUB takes 10-15 sec to show OS menu"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Canis familiaris on 2007-06-28
Hi there
I have Ubuntu Feisty installed but the GRUB takes 10 to 15 seconds to even show the menu. 
Previously when I used Dapper, GRUB took only 6-7 sec.

Can anyone help?

---

### Post by alienexplorers on 2007-06-28
Switch back to Dapper.

---

### Post by Canis familiaris on 2007-06-28
Don't you have better ideas?

---

### Post by timzak on 2007-06-28
I'm sorry I don't have any ideas for you, but I just wanted to say that alienexplorers gave the most useless advice I'd ever seen.  Maybe they were just trying to be funny, but that is NOT what a community help forum is about.  If you don't have meaningful advice, please don't post smart aleck comments.  When someone is frustrated about a problem they can't solve, that is the last thing they need.

---

### Post by diskotek on 2007-06-28
there are soe tweak/performance guides for feisty fawn. 

here all-in-one: [http://blog.lxpages.com/2007/04/24/ubuntu-performance-guides/](http://blog.lxpages.com/2007/04/24/ubuntu-performance-guides/)

---

### Post by diskotek on 2007-06-28
well my offer just to make ubuntu faster.. i'm not sure about what's happening with grub..

---

### Post by Canis familiaris on 2007-06-29
Well nothng has helped just yet. I am trying to switch to lilo from grub and see what happens.
See Ya!

---

### Post by reacocard on 2007-06-29
Are use using ReiserFS? That can take a while to mount, which slows down grub immensely. Make sure that /boot at least is on ext2/ext3 and grub will be faster.

---

### Post by Canis familiaris on 2007-06-29
Oh No! liloconfig gives an error about UUIDs! I know changing th fstab to traditional method will solve the problem? But I do not want to bother. 

Can anyone please tell me how suddenly my GRUB became slow since I used Feisty?

I remember GRUB was lightning fast with Red Hat Linux 8.0 on my PC with half the RAM. In dapper it was bit slower but fast. But it's now very slow (I can't wait 15-30 sec as compared to only 5 sec in dapper and < 2 sec in RHL 8.0).
Is there any way I can install RHL 8.0 GRUB? 
(LOL, I've scratched its CD)

---

### Post by Canis familiaris on 2007-06-29
> **reacocard said:**
> Are use using ReiserFS? That can take a while to mount, which slows down grub immensely. Make sure that /boot at least is on ext2/ext3 and grub will be faster.
No I use ext3 on /and I have a seperate /boot partition with ext3 as well.
This is my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=41ffea1e-25f3-4da1-9255-eaa94fdc67c2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=66c07666-28c5-4059-8c90-e54cfbf9c106 /boot           ext3    defaults        0       2
# /dev/hda8 # for GeeXbox
# UUID=ea94a839-a1b7-4e08-9c44-c1747a57b2de /media/hda8          ext2        noauto,user        0       0
# /dev/hda1 
UUID=2EBC379CBC375D91 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=A6002FCF002FA571 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=3067-D3DC  /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=7482332e-6c78-4ed3-9340-525b3f394f43 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by Canis familiaris on 2007-06-29
Here is menu.lst. Though I do not think it'll make any difference.
```
default		0

timeout		10


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=41ffea1e-25f3-4da1-9255-eaa94fdc67c2 ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=41ffea1e-25f3-4da1-9255-eaa94fdc67c2 ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=41ffea1e-25f3-4da1-9255-eaa94fdc67c2 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=41ffea1e-25f3-4da1-9255-eaa94fdc67c2 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

#GeexBoX Linux OS	
title	GeeXboX Media Center
root	(hd0,7)
kernel	/vmlinuz root=/dev/hda8 ro init=linuxrc boot=hda1 splash=silent vga=792 video=vesafb:ywrap,mtrr
initrd  /initrd.gz
boot
#End GeeXbox



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by sotema on 2007-06-29
Hi to all,  the same problem here but it shown up  two months after a fresh installation of Feisty. I am not sure but maybe this happened after a suspend/resume action.

I did the following:
- grub> root (hd0,0)
- grup> setup (hd0)
 without fixing the problem

also reinstalling grub didn't help.

waiting for someone to help.
my fstab follow

---

### Post by jmedina on 2007-06-30
You're lucky it only takes 10-15 seconds. Mine takes 32 seconds. For me the problem is I can not get the Floppy Drive Power Connector into the drive. It doesn't fit.:( I don't feel like making it work. I think I'm just going to start keeping my computer on. When it starts up it keeps looking for the Floppy Drive. Even though I disabled it from BIOS. Good Luck!

---

### Post by Canis familiaris on 2007-07-01
> **jmedina said:**
> You're lucky it only takes 10-15 seconds. Mine takes 32 seconds. For me the problem is I can not get the Floppy Drive Power Connector into the drive. It doesn't fit.:( I don't feel like making it work. I think I'm just going to start keeping my computer on. When it starts up it keeps looking for the Floppy Drive. Even though I disabled it from BIOS. Good Luck!

Why don't you remove the floppy drive? (You can use a USB floppy drive if you really wish)

---

### Post by Canis familiaris on 2007-07-01
I even reinstalled Feisty with /boot as a separate primary partition but no avail!

---

### Post by malcorry on 2007-07-12
I have had a frustrating 7.04 slow boot at the Grub 1.5 stage for the last two weeks then realised I had a Western Digital hard drive on its own as Primary Master so the jumper needed to be set to Single.
When installing Feisty Fawn I had moved my second hard drive to the Secondary Master position with a CD-ROM slave drive but forgot about the jumper cannot be left as Master if single drive on cable.
Check all drives are installed correctly.

---

### Post by kavon89 on 2007-07-12
GRUB shows up for literally 1.5 seconds (It says that) and then goes into booting Ubuntu. I only have Ubuntu installed so that might be the reason for the quick default. Maybe there is a time adjuster?

EDIT: I looked at the menu.lst you provided. ```
timeout		10
``` Looks to be the GRUB timer, perfect value for timeout too, 10 seconds. I would try changing it to 5 and test it out, make sure you backup that file because I'm going on a hunch here.

EDIT2: I'm a bit sleepy and I think I misread, it seems it takes 10-15 seconds just to get to the GRUB stuff correct? It might be a BIOS thing. Mine is very quick, GRUB starts up right away after the odd 5 second RAID setup my BIOS prompts me for and heads right into my default Ubuntu. I have 7.04, maybe you need a GRUB version update? :s

---

### Post by Canis familiaris on 2007-07-12
Sorry for a newbie question, but How can I reinstall GRUB?

---

### Post by MrObvious on 2007-08-09
To reinstall grub you can do sudo grub-install /dev/*** (where *** is the hard drive you wish to install to).

---

