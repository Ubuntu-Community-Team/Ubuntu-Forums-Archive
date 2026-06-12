---
title: "Formatting the MBR drive"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by xDavee on 2007-10-27
I installed Ubuntu 7.10 and i want to get Windows XP back and i have the installation CD for that. When i put the windows CD in after i press any key to boot i get a blank screen. I looked online and it said that maybe my MBR drive was corrupted. Is there anway to format the MBR drive in Ubuntu 7.10 again I do not have Windows XP and so I am not able to do anything using Windows. Please help me I need my Windows XP back. Thankyou in advance ! =)!

---

### Post by taurus on 2007-10-27
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Unicycle on 2007-10-27
Download and burn the Super Grub Disk.  It will fix all your problems.  Use it to restore the Windows MBR.

:lolflag:  Taurus beat me to it!

---

### Post by xDavee on 2007-10-27
so once i burn it onto a cd do i boot of it from from F12 or do i run it after im actually in Ubuntu ?

---

### Post by xDavee on 2007-10-27
Ok so i tired booting it from F12 and it says this device cannot be booted like it doesn't recognize it as being booted

---

### Post by Campingman on 2007-10-27
Hi xDavee,

Sorry to hear you having issues with Ubuntu, if you have your bios set to boot from cdrom first Super Grub will boot into its options from the cd.

---

### Post by Duck2006 on 2007-10-27
Can you boot into ubuntu?

---

### Post by xDavee on 2007-10-28
Well i deleted my partitions but i can boot into Ubuntu through the Live CD and I had CD first set in Bios but SuperGrub didnt work. Any Solutions? When  i was booting from Ubuntu Live CD before it went in i had a Logical Block 0 I don't know if that helps at all with my problem but i recieved taht as an error.

---

### Post by xDavee on 2007-10-29
PLeasee help me i need my windows XP baaack!

I figured out how to get Super Grub to work but could you show me how to repair/format the MBR drive.

---

### Post by Duck2006 on 2007-10-30
Boot up using the windoze xp cd
Press R for recover
At the command promp tyre

fixmbr

That sould repair your MBR so you can boot xp

Then reinstall grub to get it to dual boot.

---

### Post by xDavee on 2007-10-30
no see the problem is that the windows CD doesn't Boot at all like after Press any Key to boot i just see a blank screen and it never gets to setup and i looked online and it said that if you format ur mbr and your partition tables that it would fix that


after clicking this site scroll all the way to the bottom and in blue it shows the problem and the solution to my problem but I don't understand how to fix it + What is Zero Fill? 
[http://www.codeproject.com/useritems/installwindowsxp.asp?df=100&forumid=334362&exp=0&select=1764691#xx1764691xx]("http://www.codeproject.com/useritems/installwindowsxp.asp?df=100&forumid=334362&exp=0&select=1764691#xx1764691xx")

---

### Post by Duck2006 on 2007-10-30
What iit is doing is filling your mbr with zero's  so it has no data in it.
Have you tryed super grub cd to see if that will repair it for you?

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by xDavee on 2007-10-30
can you show me how to zero fill and i'm not sure how to use the Super Grub to set it up so that it fixes my MBR for windows

---

### Post by xDavee on 2007-10-30
PLeasee hellpp xO

---

### Post by Duck2006 on 2007-10-30
[http://supergrub.forjamari.linex.org/?section=documentation#quick_guide](http://supergrub.forjamari.linex.org/?section=documentation#quick_guide)

---

### Post by arpanaut on 2007-10-30
I installed GRUB to MBR with a Gnu/Linux distro (dual boot), and Windows no longer boots.

1) I just want to boot Windows for now, I'll fix it later,

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Windows
   4. Boot Windows

This will boot Windows for now for you and you can verify that Windows is still okay and able to be booted. You can access all your data and get any urgent work done. You can fix the problem more permanently later on when you have time or you are in a better mood.

2) I  want my MBR pointing to Windows  bootloader again  - right now!

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Windows
   4. Fix Boot of Windows



I installed Windows on a first hard disk but I unplugged it and plugged it in as a non-first hard disk. Now I want to boot it.

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Boot and Tools
   4. Boot Master Boot Record (MBR)

For further documentation:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by xDavee on 2007-11-01
Do i use 1, 2, or 3 for the installation of windows xp because i dont think i have windows xp anymore because i installed ubuntu over my windows.

See i'm trying to boot windows from a CD and when i say that i mean the Setup in order to install windows but after Press any key to boot there's just a blank screen

and this is what i get i know i already posted but this site shows you/describes the problem and how to fix it [http://www.codeproject.com/useritems/installwindowsxp.asp?df=100&forumid=334362&exp=0&select=1764691#xx1764691xx]("http://www.codeproject.com/useritems/installwindowsxp.asp?df=100&forumid=334362&exp=0&select=1764691#xx1764691xx"):Scroll to bottom part of the site

---

### Post by xDavee on 2007-11-03
Please help ^^

---

### Post by sandysandy on 2007-11-03
are u able to start win XP setup with the Win XP CD.

with win xp cd there is option to fix MBR.

my MBR had also gone for a six after installing ubuntu, but i could recover it with win xp cd.

---

### Post by xDavee on 2007-11-03
No i can't acess the CD basically i need windows back but the cd doesn't work Possibly by the MBR if you read my previous posts it lists a website that explains my problem and the solution i jus need all the help i can get -so desperate to get windows baaack:D -

---

### Post by xDavee on 2007-11-12
pleeeasee help !~

---

### Post by pistcivet on 2007-11-12
I read the post you linked to earlier, I've never seen or heard of something like this happening.
But if you want to "zero fill" a drive, the best way I know of is DBAN:
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

Download the iso, burn it, and boot to it just like any Linux distro.
Set it to zero-fill the entire drive. (It could take some time - 1 or 2 hours)

Post back here if this actually works.
I'm very skeptical. (I think you have bad hardware/loose cable etc.)

---

