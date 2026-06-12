---
title: "Installation Problem"
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by saabirsa on 2005-12-05
Hello,

I have just started the installation for Ubuntu Linux on my Pentium III box with 64MB Memory. However, whenever I try to start the installation, it either freezes in the partition (installation), or it gives me ```
Kernel panic - not syncing: Attempted to kill init!
```(Both @ the beginning of Installation and on the LiveCD.)

I am pretty sure I have the right Distro (PC (Intel x86)), but I have tried everything, including another Distro (Gentoo). This is the 1st time for me installing Linux, as I have always used some sort of Windows OS before. Any help would be appreciated :)

Thanks
Saabir Salim

---

### Post by raublekick on 2005-12-05
I'm not too sure what a kernel panic is, but I would think the problem has something to do with your RAM. 64MB won't be enough to run Ubuntu (maybe Xubuntu or Fluxbox).

---

### Post by saabirsa on 2005-12-05
OK, I just put in 2 128MB blocks, and 1 64MB, still same error.
 
Saabir Salim

---

### Post by neobloodline on 2005-12-05
Check this site out. Problem might be with your SATA driver.

[http://thefinleys.com/dell_d810/](http://thefinleys.com/dell_d810/)

---

### Post by saabirsa on 2005-12-05
I don't have a SATA drive, should I still go ahead on what it says on that site?
 
Saabir Salim

---

### Post by neobloodline on 2005-12-05
I woudn't advise you to try something that you don't have a problem with. I'll keep searching

-----

Edit :

Try referring to this Thread:

[http://ubuntuforums.org/showthread.php?t=34590](http://ubuntuforums.org/showthread.php?t=34590)

---

### Post by Terry of Astoria on 2005-12-05
Test your memory. Type memtest (or is it memtest86) from the ubuntu live disk boot prompt. Actually does the installer have it?
I have found that often Windows will run just fine on a machine w/bad RAM, and then Linux won't sometimes. THe only way to know how your RAM is is to test it thoroughly. It can tak a couple hours or more. Memtest86 has helped me save countless hours of frustration.
 (edit) you can also download memtest86 -it's a teeny-weeny iso- and burn it to cd from somewhere.

---

### Post by GAScorpio on 2005-12-05
Ok..I am having the same/similar problem with the installation. 

Note: Installing on existing Windows Me with One Full Partition.
     
Part 1:  
Partitioning Hungup at 52% 

Part 2:
Now I can not get the cdrom to Boot Ubuntu.
Bios shows cdrom in the Second of Four boot positions.
Starting to think i might have a bad cdrom

Thanks,
GA Scorpio

---

### Post by saabirsa on 2005-12-05
[quote=neobloodline]I woudn't advise you to try something that you don't have a problem with. I'll keep searching
 
-----
 
Edit :
 
Try referring to this Thread:
 
[http://ubuntuforums.org/showthread.php?t=34590]("http://ubuntuforums.org/showthread.php?t=34590")[/quote].
 
Tried the thread, I cannot load the installer sometimes, so I cannot load the modules as shown in the topic.
 
As for the memtest, Im running it now, ill tell you what happens in a few hours.
 
Thanks for all the help so far.
Saabir Salim

---

### Post by saabirsa on 2005-12-05
[quote=GAScorpio]Ok..I am having the same/similar problem with the installation. 
 
Note: Installing on existing Windows Me with One Full Partition.
 
Part 1: 
Partitioning Hungup at 52% 
 
Part 2:
Now I can not get the cdrom to Boot Ubuntu.
Bios shows cdrom in the Second of Four boot positions.
Starting to think i might have a bad cdrom
 
Thanks,
GA Scorpio[/quote]
 
Can't be a problem with my CD, I must have burned it on at least 5 CDs, with 3 diffrent downloads all verified with MD5Sum.
What are your specs?
 
Saabir Salim

---

### Post by GAScorpio on 2005-12-05
saabirsa,

Sorry for the Confusion. I was posting the same issue.
Side Note: My installation CD is All on One- :D 

I will let you know if i get any answers.

GA Scorpio

---

### Post by saabirsa on 2005-12-05
LOL, yea I noticed (same time replies) :razz: 
 
Thanks
Saabir Salim

---

### Post by GAScorpio on 2005-12-05
Whahoo!  I am on Ubuntu. 

Put an additional 128 Ram to be on the safe side and put in a new cdrom in the Slave position. Bios set to boot to the cdrom first and hd last. 

Partitioned the machine to erase the old and use the available disk space.  

Installed with no problems.  Got my New Gnome wallpaper and icons from gnome.org and new Firefox theme. Now its on to install the dvd and getting the java to work.  Going to java.com where they have the instructions.

Good Luck everyone.

GaScorpio

---

### Post by saabirsa on 2005-12-06
Woah, that is EXACTLY what i did, added 3 blocks of 128MB, and a new 52x CD-RW Drive to replace the 2x CD-ROM Drive. Lucky for you it works, same problem here :( . Enjoy your new linux installation :)
 
Saabir Salim

---

