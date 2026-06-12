---
title: "New to dual booting... A little advice maybe???"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by fiel on 2007-12-31
Hi Everybody,

I just finished downloading Gutsy and am going to install it on a separate partition.  Not really looking to use Wubi as I also have never partitioned a hard drive before; I did watch the following video on You Tube and figured it would be a great learning experience:

[http://youtube.com/watch?v=JBfl3oViny8](http://youtube.com/watch?v=JBfl3oViny8)

It looks pretty simple and I will be doing this on an old computer.  

My question is that if I install Gutsy on one partition, do I have to do anything in addition if I have to reinstall Windows XP?  I plan on cleaning out my computer so would putting in Gutsy then reinstalling a fresh copy of Windows.  I heard that when installing Gutsy it might do something to the MBR, but will I have to worry about that if I have to reinstall Windows?

Thanks.

---

### Post by The Tronyx on 2007-12-31
If you mess up the MBR you should be able to fixmbr with a recovery disk.  As far as dual booting with XP I have had very few problems though I do know that others have had more.  When you partition to dual boot, it is always reccommended to defrag your XP hard drive prior to partitioning and formatting it.  You could also refer to this, it's a pretty solid guide. [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by maybeway36 on 2007-12-31
Windows will get rid of Gutsy's boot loader, but you can reinstall it from the live CD, so there's not much to worry about.

---

### Post by Sbarton on 2007-12-31
I would say it may prove better to have XP installed first then 'Gutsy'.
If you have the XP disc you can fixmbr with that should you need to.
regards

---

### Post by krazytekn0 on 2007-12-31
The easiest thing to do if you're going to be reinstalling windows would be to do that first, and then install ubuntu. If you do this the dual-boot will be automatically set up for you. PAY CLOSE ATTENTION TO THE INSTALLATION INSTRUCTIONS THOUGH. Don't just click through stuff. READ.

---

### Post by fiel on 2007-12-31
Now when I reinstall a fresh copy of Windows, will I still need to defragment my hard drive?

Also (for future use) to clarify what maybeway36 noted:
When I do reinstall Windows, will I also have to format the separate Partition with Ubuntu and reinstall it before running the live CD to fix the boot loader?

Thanks the help.

---

### Post by Paqman on 2007-12-31
> **fiel said:**
> Now when I reinstall a fresh copy of Windows, will I still need to defragment my hard drive?

If you're reinstalling Windows you'll have to format the Win partition anyway. Since that will delete all the files there would be nothing to defragment.

> 
Also (for future use) to clarify what maybeway36 noted:
When I do reinstall Windows, will I also have to format the separate Partition with Ubuntu and reinstall it before running the live CD to fix the boot loader?

Thanks the help.

Nope, you can fix the GRUB boot loader without reinstalling Ubuntu.

Incidentally, you'll actually have to make at least two partitions for Ubuntu. One for the main system, and  another tiny one called a swap partition. The installer can do this automatically for you.

---

### Post by kellemes on 2007-12-31
You better install Windows first..
Use the partitioner on a livecd or a Windows-partitioner to create room for Ubuntu. Install Ubuntu.. the installer will put Windows in your bootmenu automagically. If not..  You can always add Windows to the bootmenu.

When things go wrong with the bootloader, no worries..
You can always use [SuperGrubDisk]("http://supergrub.forjamari.linex.org/") to fix your bootloader, it can fix Grub (the Linux bootloader) **and** fix the Windows-bootloader if you don't want to dualboot anymore.

---

### Post by hums07 on 2007-12-31
> **fiel said:**
> Now when I reinstall a fresh copy of Windows, will I still need to defragment my hard drive?

Definitely not. And if you install Windows on a separate partition, you don't need to touch that partition. You will need to defragment only if you have one partition (on which you have Windows) and you want Ubuntu tries to create a partition out of the free space of that partition.

---

