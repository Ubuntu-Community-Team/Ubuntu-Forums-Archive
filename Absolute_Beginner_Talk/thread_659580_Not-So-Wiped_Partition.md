---
title: "Not-So-Wiped Partition"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Vinylcake on 2008-01-05
'Ello.  Several months ago, I installed Ubuntu 7.  It made its own partition on the second half of my HDD which also has my Windoze XP install.  Being an idiot, I got a hold of Partition Magic and deleted the ext3 partition and moved some of its space to my NTFS partition and made another partition which I wanted to use for media.  After restarting, I was met with a GRUB 17 error.  My lovely little box also now refuses to boot from a CD.  Soooo, I'm not quite sure what I should do.  Suggestions?

---

### Post by empthollow on 2008-01-06
well, if you can't boot a cd it's probably a setting in the bios, usually has to do with boot order.  without using a cd you can use the grub command line. there should be a message at the bottom of the screen telling you to press a button - i think it's c - for command line.  here is a page that can help you with the details [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

here is what you need to do once in the command line.  i will instruct to boot windows because it sounds like your linux may be messed up do to the partition magician.

```
grub>  find /boot.ini
 (hd0,0)
```
[CODEgrub>  rootnoverify (hd0,0)][/CODE]
```
grub>  makeactive
```
```
grub>  chainloader +1
```
```
grub>  boot_
```

---

### Post by bwtranch on 2008-01-06
Sounds like a mess. I would start over.

---

### Post by empthollow on 2008-01-06
it'd be much easier if you could boot from cd, you can reinstall windows bootloader from the install disk.  that will erase grub. you can also reinstall grub from the ubuntu disc.  ahh the catch 22's.  i remember when i was trying to install win95 and i needed cdrom drivers to read the cd.. then i thought to myself YES, I HAVe them on the cd..... wait.... that's not useful....

---

### Post by Vinylcake on 2008-01-06
Okay, I see.  All I'm really interested in is getting rid of Grub and forgetting I ever put Linux on there.  :P  So installing Windoze somewhere would do that?  I have a CD handy for Windoze 98--would installing that on a FAT32 partition do it?  I honestly don't have too strong a grasp of what grub is besides that menu.

[QUOTE=empthollow]well, if you can't boot a cd it's probably a setting in the bios, usually has to do with boot order. without using a cd you can use the grub command line. there should be a message at the bottom of the screen telling you to press a button - i think it's c - for command line. here is a page that can help you with the details [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)[/QUOTE]
Grub doesn't even load up.  :P  I can boot off my slave Win98 HDD (extra crippled and useless), but not my master or a Linux CD.

---

### Post by empthollow on 2008-01-06
well, i'm not sure how to fix it with win 98, starting with 2000 you can boot the cd, press c for console, login, and type fixmbr and it will restore the windows boot record.  i don't think i've ever had to do it with 98 but they may have put the same thing on there.

---

### Post by bwtranch on 2008-01-06
No, I tried that on my Compaq that has Windows 98. Didn't work. Windows 2000 was a good OS. The first one that really lived up to the promises. XP Pro isn't bad either. After that, forget it. MS just went downhill.

---

### Post by thelatinist on 2008-01-06
> **Vinylcake said:**
> Grub doesn't even load up.  :P  I can boot off my slave Win98 HDD (extra crippled and useless), but not my master or a Linux CD.

Booting from a CD happens before Grub starts, so that's irrelevant.  If you can boot from a Windows install CD and not from the Ubuntu LiveCD, there is probably a problem with the CD itself.

---

### Post by empthollow on 2008-01-06
if memory serves most of the win98 cd's aren't bootable.

---

### Post by bwtranch on 2008-01-06
Well, that's true, unless it is a "rescue" CD. Most likely distributed by third party vendors. Like my Compaq.

---

### Post by empthollow on 2008-01-06
ahh, if it's a rescue cd you probably won't be able to boot to console though.

---

### Post by rkd on 2008-01-07
Your problem is easy to fix.

The first step is to get your computer to boot from the CD. It did so some time ago, so it should not be very hard to get it to do so again.  Most likely you did something that had the unintended effect of changing the sequence of devices the computer looks at when trying to boot. To correct this, you need to get into your setup menus when you are starting or restarting your computer. You probably know how to do that. If not, ask and we can talk you through it. Once in the setup menus, find the one that controls which order the computer looks at devices when booting. If the hard disk is before the CD, change things until the CD is before the hard disk.

Once you have the computer booting from the CD again, there are at least two ways to fix the GRUB error 17 problem.

1. If you have a Windows XP Install CD, boot from it, choose the recovery console, and run the fixmbr command. You usually cannot do this with a Restore CD - you need an Install CD, which is rarely shipped with PCs these days.

OR, if you don't have a Windows Install CD,

2. Boot from a Super GRUB CD, choose Windows from the main menu, then choose Fix Boot of Windows. See below for where to get Super GRUB.

Either of the above approaches will restore the MBR at the start of the disk to the state it was in before GRUB was added, and the computer will boot directly into Windows.

If you need to get Super GRUB, the web site is:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

It is a confusing site, but the download links are right at the top of the page. Don't let the clutter confuse you and you'll find them easily. The .iso is less than 4 MB, so it doesn't take long to download. Then burn a CD with it the same way you did the Ubuntu .iso and you'll have a bootable Super GRUB CD.

---

### Post by Vinylcake on 2008-01-09
The Fixmbr command did the job for me.  It turns out, the CD was actually the problem when trying to boot off of it, as someone suggested.  Thank you all for the help.

---

