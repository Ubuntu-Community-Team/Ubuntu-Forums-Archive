---
title: "Restoring GRUB after XP formatting"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Xorg.conF on 2007-12-16
Well I've had this problem numerous times, as some of you would know, Windows XP needs to be formatted many times in order to keep its integrity at top shape and because of the errors/virus yes those to.  But formatting erases the GRUB boot menu, I have tried many different ways to restore it but all failed.  There must be a dozen ways, as I found them all through google but I just end up formatting my Ubuntu in the end.

Does anyone know of a way of properly achieving a restoration of the Unified Bootloader, AND has tried it themselves to vouch it will work 100%  I need this to work people!


Thank You in advance for all the help.

---

### Post by LaRoza on 2007-12-16
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Xorg.conF on 2007-12-16
Well it may be because I did it wrong, but I followed the instructions.  It did give me back the menu when I turn on my laptop, but when I select Ubuntu os at the top, it gives me an error, File Not found... .  Although windows still worked nicely (how nice now I have to use Windows on a 10gb partition), everything else failed to boot.

---

### Post by Xorg.conF on 2007-12-16
when I choose Ubuntu it gives:  Error 15: File not found

    Press any key to continue...
it then takes me back to the menu

I dont want to format my linux partition, please anyone who knows how that works help

---

### Post by shadow-of-sin on 2007-12-16
You may want to use Super Grub Disk instead, here's a guide for it:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by HDave on 2007-12-17
Do not reformat your Ubuntu partition...I am sure it is not necessary.

I am not the GRUB expert, but I have had this error before and gotten past it.

You need to have your GRUB menu items line up exactly with what is in your boot directory and, specifically, the name of your kernel.  A generic GRUB installer will probably not get it right.

There are a number of Windows utilities that will allow you to (in Windows) mount your Ubuntu partition and peruse the files.  I use the one here:

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

Take a look at your files and then edit your GRUB menu to match.

Google "GRUB Error 15" and you will learn more than you ever wanted to.

---

### Post by Xorg.conF on 2007-12-17
Do not reformat your Ubuntu partition...I am sure it is not necessary.

I am not the GRUB expert, but I have had this error before and gotten past it.

You need to have your GRUB menu items line up exactly with what is in your boot directory and, specifically, the name of your kernel. A generic GRUB installer will probably not get it right.

There are a number of Windows utilities that will allow you to (in Windows) mount your Ubuntu partition and peruse the files. I use the one here:

[http://www.fs-driver.org/](http://www.fs-driver.org/)...



This is a good idea but I have ReiserFS not Ext2, but the idea of editing the GRUB file still might work from a live cd.

about that super grub disc, I tried that just before I saw your post, i followed:

I reinstalled Windows and Linux no longer boots.

boot your SGD floppy disk, USB disk or CD-ROM 
English Super Grub Disk 
Gnu/Linux 
Fix Boot of Gnu/Linux (GRUB) 
select your Linux partition 
see message, 'SGD has succeeded' 
you're done! reboot 


That and still error 15, and not sure if I got the SGD has succeeded.  But I think that this works with only if u have an actual "dual boot", one partition for Win and one other for Ubn, but my Ubuntu has 3 partitions in it, / and /home and a swap of course so there is still a chance the SGD will work I just need to use the right method.

---

### Post by Xorg.conF on 2007-12-17
Well I have good news and bad news.

I have successfully fixed the error 15 error, took the advice of editing the menu.lst, seems what was wrong was that it was pointed to (hd0,2) but the file that it wanted was in my root partition so I simply changed it to (hd0,1) and it worked.  I now can boot back into Linux

But the prob is, that before I did that, I used a method found at this thread:  [http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261) .  it was : 

Fixed this by doing a text-based grub install off the 6.10 cd. After going through the language settings, hit escape to get to the main menu. Select "install grub" and it will bring up the partitioner. Set the correct mount points in the partitioner, and make sure that the partitions will NOT be formatted. It will then say something about installing a base system, hit escape or no. It should then go to the grub install prompt. Do that, reboot, done......

well I did that but there was no "It will then say something about installing a base system, hit escape or no" it just went strait to installing the base system..... I stopped it at 6%...

so the result was the problem mentioned in the good news, I fixed it by hd0,1.  but I think it also corrupted my /boot and other folders, now my wireless doesn't work, I no longer have internet.  and now the name of my computer is x1-6-00-14-22-98-af-00...like in terminal it says x1-w/e@folder....    and there's other wierd probs



so I've now decided to format my Linux partition, so now i have to redo all my setting etcc 300mb of updates+programs

---

### Post by HDave on 2007-12-17
Sounds like the SGD set up your GRUB menu to boot from the wrong parition (i.e. /home or /swap).

Another thing you can try.

Little known fact, but you can change the command lines of GRUB menu items directly from within GRUB.  It won't save it to disk, but will allow you to try different things.

When the GRUB menu comes up, highlight the menu item you want, and hit "e".  I *think* once you are looking at the menu command you hit "e" again to edit.  Change the partition name to the correct one (or perhaps the kernel name) then hit "b" to boot from your edited GRUB menu item.

I may have the keystrokes a little off here, but since it doesn't save your edits back to disk there is nothing you can damage....

---

### Post by HDave on 2007-12-17
> ... so now i have to redo all my setting etcc 300mb of updates+programs

OH NO!  :(

I am sorry for not catching you in time...I really am.

Good luck with your new install.

Wish there was an Ubuntu Grub wiki that covered all this...

---

### Post by Xorg.conF on 2007-12-18
Well from this experiance, I've learned enaough never to have this problem again.  Thx for all the help no more questions.

---

