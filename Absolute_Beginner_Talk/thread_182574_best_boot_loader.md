---
title: "best boot loader?"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by erniewinner on 2006-05-26
:confused: hi all,

i've been faffing with boot loaders in an attempt to get what i want... win98 ( x 2 or more), xp, ubuntu and xandros. i need xp for big brother.
i couldn't find a reasonable way to reinstall bootloaders to my satisfaction if a problem arose. i have gone back to a third party boot loader. "osl2000" let me hide patitions. but it wouldn't boot ubuntu... xandros was ok. so i tried "bootitng" i now have win98, xp, ubuntu, xandros. but ubuntu won't boot. in bootitng it says ubuntu is not bootable. i took a look using partion magic and there is nothing different to it than my xandros install well apart from the ( /). 
i would like to know why it won't boot and how to get it going...
i have tried to install with no boot loader and also installed grub then reinstalled bootitng over the top. ( for the sake of it.) and it doesn't work. i want to stick with bootitng and ubuntu... thanks.

oh one thing that comes to mind my hd is 20 gigs the ubuntu partition boots ok with grub from the partition that is near the end of the disk (where i want it) but bootitng says it might not be bootable because of where it is... i'll give it a go installing in the 8gb limit (for the sake of it.) but after that i'm lost.

---

### Post by bruce89 on 2006-05-26
What was wrong with GRUB?

---

### Post by erniewinner on 2006-05-26
grub won't let me hide partirions and more complex operations like backup and restore etc. but the ubuntu grub installer won't boot xandros... and i couldn't get a easy way to reinstall it without a full install of ubuntu... :-k

---

### Post by Sef on 2006-05-26
> i couldn't get a easy way to reinstall it without a full install of ubuntu

Here's an easy way:

[Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by Sef on 2006-05-26
> grub won't let me hide partirions and more complex operations like backup and restore etc.

That's not true.  Check this out:  [GRUB_Manual]("http://www.gnu.org/software/grub/manual/html_node/")

---

### Post by erniewinner on 2006-05-26
mmm... bootitng is point and click and i like that... i tried several times with the cd and custom options and it kept installing ubuntu... even if i went to the menu (press escape and then "install grub...") and even if i succeed it won't load xandros.

i think i like the point and click for  backup and restore etc. when i asked before no one seemed to know about complex grub options... 

honestly i just need to get ubuntu bootable. i don't know why it isn't when xandros linux is as well as xp and 98. both third party apps seem to think ubuntu is not bootable. is there a flag i can turn on? what else should i be looking at in the way of the partition? thanks.

---

### Post by erniewinner on 2006-05-26
8) [http://www.terabyteunlimited.com/kb/article.php?id=279](http://www.terabyteunlimited.com/kb/article.php?id=279)

ha! should have looked here first. hope it works... :rolleyes:

---

### Post by youthforlinux on 2006-05-26
wat is everyone elses favorite bootloader?

---

### Post by Sef on 2006-05-26
> youthforlinux  	wat is everyone elses favorite bootloader?

You should start a new thread for that question.  Otherwise it looks like you are hijacking this thread, which I am sure is not your intention.

---

### Post by erniewinner on 2006-05-27
8) i am liking bootit ng although i had to get used to how it works... and its a bit weird till you get used to it, at least coming from hyperos... what i like is you can make configs for drives then boot them with one click. and only the drives you want get booted. ie i have 6 or 7 partitions on disk but i can choose a config to boot just 2 of them ie xandros and swap (i am in the process of getting ubuntu up) all the others are hidden. 

it's got to be said i did lose my whole drive while trying to get used to it... but there was nothing important threre... and one important thing is to make sure another os is in the config while installing ubuntu or ubuntu will write over the mbr without asking...

[http://www.terabyteunlimited.com/kb/article.php?id=279](http://www.terabyteunlimited.com/kb/article.php?id=279)

---

### Post by erniewinner on 2006-05-27
oh yeah and also reinstalling the boot loader is just a question of running the bootit cd... (which you burn from an iso.) thats alot easier for me. i can easily remember to do that!

---

### Post by erniewinner on 2006-05-28
i'm real happy with bootit ng except i still can't get it to boot ubuntu... (i am happy i have win98 xp xandros.) the guide says the key is to install grub to the root partition. i just can't seem to get it to work... i can't use a floppy as i don't have one on my laptop, can i make a boot cd??? i know i might be able to boot the ubuntu partition with suse 10 as it had that option. (i can't find it... it's here somewhere.) the ubuntu option is to boot "first hard disk" which in my case is no good... and i can't make ubuntu the first patition as it is tools for bootit ng. thanks. :-k

---

### Post by catlett on 2006-05-28
With grub there is no need for hiding partitions etc. Grub boots to the partition you want and that os runs whatever partitions it wants. You're making your life difficult. Install grub and then edit the menu list with entries for your other os's. 
This will show you the power of grub [http://www.justlinux.com/forum/showthread.php?threadid=143973](http://www.justlinux.com/forum/showthread.php?threadid=143973)

---

### Post by erniewinner on 2006-05-28
i don't like all my partitions or drives exposed to the net when their is no need to be. i feel i have to disable them through the disk drive app. grub wouldn't pick up my windows 98 installation and it won't boot xandros. :-?

---

### Post by catlett on 2006-05-28
Good poimt about exposing partitions I didn't think of that but can't you just keep them off your /etc/fstab and then they won't be mounted and therefore unaccessable?
You have to edit grub like the guy in the link did.
Just put in an entry for the partition your windows and xandros drives are on.
If you had grub installed from ubuntu you would do it like this```
 sudo gedit /boot/grub/menu.lst
``` Then add an entry at the bottom for windows
```
title		Windows 
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
This entry assumes windows is on the first hard drive and on the first partition (hd0,0) Grub uses 0 as a place so 1st drive is 0, 2nd drive is 1 etc Same with partitions 1st partition on first hard drive hd,0,0, 2nd partition on first hard drive hd0,1
Then add one for Xandros 
```
title          Xandros 3.0 
root           (hd?,?)
chainloader    +1
```
A generic grub entry is setup like this 
```
title     "OS's name"
rootnoverify    (hd?,?)
chainloader     +1
``` All you need to do is find out what partition the os is on. In ubuntu you can run fdisk -l for a listing of partitions. The title doesn't mean anything to grub. It is for your reference so it doesn't matter if you don't have the correct name of the OS. You can use root and rootnoverify. I have never gotten an error message with rootnoverify but I have had a couple of issues with root.

This is my grub list just for reference
```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.15-18-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-18-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-18-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-18-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-18-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-18-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Debian GNU/Linux, kernel 2.6.15-1-486 (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-1-486 root=/dev/hda7 ro 
initrd		/boot/initrd.img-2.6.15-1-486
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda7.
title		Debian GNU/Linux, kernel 2.6.15-1-486 (recovery mode) (on /dev/hda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-1-486 root=/dev/hda7 ro single 
initrd		/boot/initrd.img-2.6.15-1-486
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title       PC BSD
rootnoverify (hd0,3)
chainloader +1
boot
```

---

### Post by erniewinner on 2006-05-28
i think thats all a bit advanced for me yet... while i'm not fussed with this laptop. my idea was using linux on a computer i regard as mission critical. i was happy with a floppy in the old days and wouldn't mind the boot time rather than have me mess up anything in my trials. i have a real job remembering stuff so i have to go with the way i can work... i found it easy to have a floppy with "fedora" on or "ubuntu" in this case... i wouldn't neccessarily boot into it that often on that machine but it would be nice to!

---

### Post by erniewinner on 2006-05-28
:cool: ha! i'm in, i was losing hope but i tried fedora 3 no good... installed fedora 4 got it to work and found out my partition was dev/hda1... seems it changes depending on which you select and where you place them in bootit ng. anyway job done i'm happy!

---

### Post by catlett on 2006-05-28
That is the best post in this thread yet. Glad you got it working even with my bad advice:-D 
P.S. I try and post the exact procedure that worked even if noone in the thread asks or even if the thread responses didn't work. Because someone might google bootitng and dual booting linux with the result being this thread. Just when they get to the bottom and the guy says it works they find out he doesn't elaborate. :shock: 
Anyways glad you worked it out in spite of my replies:eek:

---

