---
title: "Dual Boot Problem"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Ht228 on 2008-04-03
Hi, first post on this forum, and unfortunately I'm looking for some help...

I converted to ubuntu a few months back, and its great, but I missed a few of my old windows programs, Sony ACID and Reason 4.0 (neither of which would run in WINE). 

After a while I started to pine for my old programs, unable to find a linux equivalent. So I decided that I could try to dual boot windows xp and ubuntu.  

I found this guide after a quick googling ([http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm))
which seemed to walk me very nicely through the whole process in a manner which I could comprehend. 

I got about half way through, no problem. But when it came to reinstalling GRUB, I hit a brick wall. I had windows installed, aswell as the previous ubuntu installation. But I can't find a way to log back into ubuntu.

I've tried telling the system to boot ubuntu first, but all I got was an error message, or nothing at all. I then decided to delete the windows partition, hoping to just return to the way things were. But I got the same error message.

I can now only get into a bare bones version of xp (without internet), and can't get into ubuntu at all; very annoying. Ideally, I'd like both partitions working, but if anyone could get me back to the starting position at least I'd be very grateful. 

Sorry for the wall of text, but can anybody help me out?

---

### Post by bumanie on 2008-04-03
It would help if you could post the error message. Is it a grub error or some other error?

---

### Post by metaphor- on 2008-04-03
GRUB tends to rather nasty to remove. From the sounds of things your MBR table has to be reset. If you have your windows xp cd, boot from it at the start, and select the recovery console then type

fix /mbr

this should completely removoe grub and install the default windows boot loader. Im not sure if that will allow ubuntu to be selected from boot, so id recommend looking into reinstalling grub.

also, windows can not read ext3 or Ubuntu partitions. You may have accidentally deleted ubuntu. I would recommend using a third party hard disk examiner like partition magic to see if your partition for ubuntu still exists.

---

### Post by maybeway36 on 2008-04-03
If you can boot the Ubuntu live CD, go to the terminal and type:
```
sudo grub
root (hd0,0)
setup (hd0)
```
This will only work if your Ubuntu install is on partition 1 of the main hard drive; otherwise the (hd0,0) should be changed.

---

### Post by Ht228 on 2008-04-03
> **bumanie said:**
> It would help if you could post the error message. Is it a grub error or some other error?

Sorry, I forgot that.

When windows is installed, I just go straight into XP with no choice. 

Booting with only a ubuntu partition, having deleted windows:

> Operating System not found
_


When I use Gnome Partition Editor to flag ubuntu to boot, I get the message:

> Error loading operating system

> 
GRUB tends to rather nasty to remove. From the sounds of things your MBR table has to be reset. If you have your windows xp cd, boot from it at the start, and select the recovery console then type

fix /mbr

this should completely removoe grub and install the default windows boot loader. Im not sure if that will allow ubuntu to be selected from boot, so id recommend looking into reinstalling grub.

Thanks, I'll try this.

---

### Post by Endwin on 2008-04-03
> **Ht228 said:**
> Sorry, I forgot that.

When windows is installed, I just go straight into XP with no choice. 

.

That means the the master boot record is setup for windows, and GRUB is not installed. If you just get

```
 Operating System not found
``` 

That is Windows saying it cannot find the OS. If it were grub I think the error is GRUP Error 15 which you are not getting. 

If you have linux on there then you just need to reinstall grub and it should autodetect windows and setup a list for you.

Assuming of course you have windows installed BEFORE you install grub/linux

---

### Post by metaphor- on 2008-04-03
oops, ive been using ubuntu so much for the lab i wrote the syntax for fixmbr improperly


It is just fixmbr in the console

If this does not show ubuntu when you reset your system, then you have to map the drive to ubuntu from the windows boot.ini file.

---

### Post by lswest on 2008-04-03
Well, there's a link to a how-to i wrote on restoring bootloaders in my sig (second line) Maybe have a look at that?

---

### Post by Ht228 on 2008-04-03
Thanks guys. I'm working my way through what you've given me.

---

### Post by lswest on 2008-04-03
No problem, hope it helps!  Good luck.

---

### Post by hessiess on 2008-04-03
you can use supagrub disk to fix bootloaders easely, it can also boot a pratition.

---

