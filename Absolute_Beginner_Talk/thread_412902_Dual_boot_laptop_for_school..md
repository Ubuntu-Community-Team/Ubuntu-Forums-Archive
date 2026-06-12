---
title: "Dual boot laptop for school."
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by tehbeermang on 2007-04-18
I ordered a cheap refurbished laptop for school, something I can "break" without my wife getting upset with me. Doesn't come with an OS or a floppy drive. Comes with built-in 802.11b, 256m ram, 20g hd, PIII1.2ghz and a CD rom. Dell C610.

My school is part of the Microsoft Academic Alliance. I am eligible to receive specific software licenses for little or no cost. I haven't received my confirmation just yet, I'm told it takes a bit of time. I'm going to need .NET for school. 

First question: how do I go about partitioning/formatting without a floppy?

Second question: can I install Ubuntu first and then WinXP Pro? (I can Ubuntu anytime, I'll wait for a legitimate XP Pro installation) Will WinXP hunt down Ubuntu's presence with extreme prejudice?

Or should I install Ubuntu as if I never planned on windows, use it for a while (with my USB ThumbDrive as my document storage), then blow away the HD when my academic alliance confirmation arrives, install Win, then Ubuntu?

---

### Post by annda on 2007-04-18
ubuntu installer includes a very good partitioner.

windows will kill your bootloader but not your ubuntu installation. you can easily reinstall GRUB later with ubuntu's live cd.

here is a howto you can bookmark for future reference:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by LaRoza on 2007-04-18
You have a cd rom, use gparted to repartition, format your hard disk.
You 

You must install Windows first. (or not at all)

You can install then erase Ubuntu then reinstall it after you get Windows. If you are getting Windows soon, you can get a live version of Linux, Slax and Knoppix (recommended by me), and save on your flash drive. If you have an Ubuntu live cd you could use that also.

You can get many windows programs working on Linux, check out 

[http://appdb.winehq.org/](http://appdb.winehq.org/)

you can even get .NET I think.

---

### Post by vijayanand_sodadasi on 2007-04-18
I am not sure if you can installed Windows over Ubuntu without destroying anything.   Emm, does it have a CD drive?  Well sorry, I assume it probably has because you are planning to install Windows stuff.  You can install Windows first and then use the ubuntu install cd to partition the disk while installing ubuntu.

---

### Post by LaRoza on 2007-04-18
If you are getting Vista, you have to do things slightly differently.

You must resize the partition with Vista and not Ubuntu or other Linux tool.

---

### Post by RobsterUK on 2007-04-18
If you want to dual boot, the easiest way to go about it is to install Windows first, then install Ubuntu.

If you do it Ubuntu first, when you install windows it will break the Ubuntu boot loader. It is possible to fix that but its a lot easier to do it WIndows first.

---

### Post by seetho on 2007-04-18
You should not install WinXP after you have installed Ubuntu.  XP will overwrite your GRUB and you will no longer be able to boot your Ubuntu.

Always install WinXP first then Ubuntu.

However with the specs you have on your notebook it will really have a tough time with XP.

---

### Post by freebird54 on 2007-04-18
Things look a little  confusing here.  Here is what I would do with this situation.

1. Get Ubuntu.
2. Partition the drive, leaving EMPTY SPACE sufficient for whatever version of Windows you will eventually use.
3. When you get Win, install it to the empty space.
4. Use Ubuntu Live CD to re-install Grub (the boot loader) - and then edit its config file to recognize Windows as well.

Result: Dual-booting system with minimal disruption.

Simple, right? :)

EDIT:  I hope it isn't Vista you get - not because the setup won't work (it will) but because on that system it will be PAINFUL!

---

### Post by old_geekster on 2007-04-18
You can use a CD/DVD drive for the install.  Download the LiveCD and install from it.  The partitioning will be done for you, if you don't feel comfortable doing it.

The recommended way to setup a dual-boot XP/Linux is to install XP first.  I believe that this is due to the fact that Linux will recognize XP (NTSF), but XP won't see Linux (Ext2/Ext3) on the drive.

As I said, this recommended.  Will the other way work, yes.  However, I have never attempted to do it that way.  I want to take the route with the least possibilities for failure.

If you are going to install Ubuntu, I would recommend Dapper 6.06.  The reason, Edgy 6.10 is as the name states, "on the Leading-Edge of technology".  The memory that you have (256MB) is the minimum recommended for Edgy.  Of course, there are many distros available for you to choose.

My preference is Ubuntu all of the way.

---

### Post by Doug11 on 2007-04-18
> **freebird54 said:**
> Things look a little  confusing here.  Here is what I would do with this situation.

1. Get Ubuntu.
2. Partition the drive, leaving EMPTY SPACE sufficient for whatever version of Windows you will eventually use.
3. When you get Win, install it to the empty space.
4. Use Ubuntu Live CD to re-install Grub (the boot loader) - and then edit its config file to recognize Windows as well.

Result: Dual-booting system with minimal disruption.

Simple, right? :)

EDIT:  I hope it isn't Vista you get - not because the setup won't work (it will) but because on that system it will be PAINFUL!

I agree. I dual boot vista and Ubuntu and that would be the easiest way to go about it. Leave some free space for a future OS unless you feel like reformatting everything all over again.

---

### Post by N Clement on 2007-04-18
*If* you install Ubuntu first, when it sets up Grub the first time, it will obviously not add windows automagically.  When you reinstall Grub right after installing XP, it may just change the mbr, and not add XP automatically.  So, if you end up needing to edit your grub configuration file, at /boot/grub/menu.lst on the Ubuntu partition, here is an example (what mine looks like):

```
...
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-generic, nosplash
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro vga=792
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

#title		Ubuntu, kernel 2.6.17-10-generic
#root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
#initrd		/boot/initrd.img-2.6.17-10-generic
#quiet
#savedefault
#boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

You will only edit after ### END DEBIAN AUTOMAGIC KERNELS LIST.

My system partitions will almost certainly not be the same as yours, you will have to check.  However, it is coincidence that XP could possibly install on the second partition of your hard drive, so the

```
root (hd0, 1)
```

line would be correct.

You may want to lookup some more info on grub before you attempt to edit /boot/grub/menu.lst.

---

### Post by tehbeermang on 2007-04-18
Holy cow, you all are fast with replies!

I like the liveCD approach until XP Pro arrives. I've got a couple of those (Gnome and Knoppix), used them for my intro to unix class last term, I didn't have time last term to fix things if I broke them. Figured it was the safest route.

Thanks for all the help.

---

### Post by freebird54 on 2007-04-18
DO a quick searchj for 'persistent LIve CD' if you dsecide to go that route.  Methods covered include using a flash drive, or a small partition at the 'end of the disk' or even a CD-RW.  That would be another usable way to go - ***IF*** you can take the speed off the CD!

I stand by my first recommendation though :)

---

### Post by tehbeermang on 2007-04-19
Speaking of "speed off the CD", starting OpenOffice from my Knoppix LiveDVD was faster than running OpenOffice from the HD in WinXP Home. 

+1 for Linux. ;)

I guess I could leave 7gb at the end for Win and the two apps I know I need (VB.NET/MSAccess) and call it a day. 

FedEx says the laptop will be here Sat. I'll probably have a torrent of questions then. I've never actually installed Linux.

---

### Post by tehbeermang on 2007-04-21
Okay, so "no software" on the product description means it comes with XP Pro SP2 and a bunch of dell bloatware preinstalled. Basically a "Dell Value" system. I won't complain for $263 shipped to my door.

It also means I worred about nothing, but learned a lot in this thread. I can simply follow the tutorials.

It's currently downloading/installing the 53 security updates for Windows. +2 for Linux. :D

---

### Post by tehbeermang on 2007-04-23
Just an update: Feisty desktop installed flawlessly last night, surprised me by making the wireless work without issue.

I also enabled the "desktop effects", listed as a "technology preview" within the system menu. Makes me want to try making beryl/compiz work.

Thanks everyone!

---

### Post by freebird54 on 2007-04-23
The tech preview *IS* Compiz so its already working!  Getting all the effects to work is a bit tricky though, unless you can install **gnome-compiz-manager** either by Synaptic (easiest) or from the command line.  It allows you access to the setting so you can see what they are!

Enjoy!

---

### Post by tehbeermang on 2007-04-23
[http://www.compiz.org/Gnome_Compiz_Manager](http://www.compiz.org/Gnome_Compiz_Manager)

This looks intimidating. But then partitioning a hard drive and installing a second operating system for the first time is, too. 

It's important to have goals in life, even if it's to show off to my friends, otherwise I wouldn't learn anything.

---

### Post by freebird54 on 2007-04-23
If you did it that way, it *IS* more intimidating!  However, it was in the standard, already defined repositories last I looked, so just install it through System->Administration->Synaptic Package Manager (select Search, fill in gnome-compiz, hit <enter>, click check box next to gnome-compiz-manager, select Mark For installation and Apply).  Much easier to do than explain here!  It will show up in your System->Prefernces menu as GL Manager or some such (not on Feisty right now).

Of course the other way might be more 'fun' ??

---

### Post by tehbeermang on 2007-04-23
You rock!

It's like the first time I fired up that commercial OS that shall remain nameless, lots of options, no idea where to begin. If only the internet had existed like this, then...

---

