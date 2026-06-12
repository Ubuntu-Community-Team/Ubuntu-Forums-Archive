---
title: "Installation failure"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by DalgetyDad on 2006-10-17
Hi, I'm looking for help to overcome an inability to install Ubuntu on to an elderly HP Pavilion - Athlon 900, Phoenix BIOS, 256MB RAM.
I have tried Breezy Badger, Dapper Drake and even 6.10 Beta but all attempts fail at various points in the file loading process from 18% to at best 50% when everything just freezes.
I have been trying to install on to a 6GB Samsung hard drive which has been given a complete all clear by Norton Disk Doctor.
Any suggestions would be much appreciated.

---

### Post by Kateikyoushi on 2006-10-17
Did you try to install it in safe video mode ? Using the alternate install cd might be a solution.

---

### Post by Dinerty on 2006-10-17
Due to your hardware specifications I recommend you install something less demanding on your system.

[http://www.xubuntu.org/](http://www.xubuntu.org/)

Or like previously mentioned you could try the alternate CD install which is text based

---

### Post by DalgetyDad on 2006-10-17
Tried to install in safe graphics mode. System froze up at 22%.

---

### Post by deadgobby on 2006-10-17
I agree with above post. Xubuntu is your best bet for now.

---

### Post by DalgetyDad on 2006-10-17
I'll try Xubuntu but it seems all wrong when Dapper Drake is running on the lower specced machine beside this one.

---

### Post by DalgetyDad on 2006-10-17
Tried Xubuntu. It got as far as 23% installed before it froze up. Could it be that Micro$oft have got in on the act?

---

### Post by DalgetyDad on 2006-10-18
Perhaps my problem lies with the partitioner. When I inspect the hard drive after an aborted install I see that there has been no change actually made to it even though the installation script claims that partitions for / and swap have been created. Does this ring any bells with anyone out there?

---

### Post by gn2 on 2006-10-18
> **DalgetyDad said:**
> Perhaps my problem lies with the partitioner. When I inspect the hard drive after an aborted install I see that there has been no change actually made to it even though the installation script claims that partitions for / and swap have been created. Does this ring any bells with anyone out there?

You mentioned Windows, are you dual-booting?

If not, best bet I've found for installing is to create a single Fat32 partition covering the whole drive, before running the install.
When installing from live CD, just accept the default partitions during Ubuntu install, and let it sort it out on it's own.

Your hardware is well up to running Ubuntu 6.06, the laptop I'm using Ubuntu on is P3 500, 192mb Ram, and runs well enough. (isn't a rocketship though)

---

### Post by Ashrael on 2006-10-18
Have you tried the live cd first? this will give you a nice peak into waht hardware will work or not...You can also install from there and do the needed diskchecks, it might be a bad block or so....Your hardware is (in theory) up to the job, it's about 20% faster than my system (Armada M700, with 384 Mb and 12Gb) wich runs 6.06 perfectly!!

---

### Post by Bartender on 2006-10-18
Ubuntu hangs on my PC early in the process, when it's detecting hardware.  PCLinuxOS flew right through the parts where Ubuntu hung.  Might want to try a different flavor of Linux.  See if it does the same thing.

---

### Post by gn2 on 2006-10-18
> **Bartender said:**
> Ubuntu hangs on my PC early in the process, when it's detecting hardware.  PCLinuxOS flew right through the parts where Ubuntu hung.  Might want to try a different flavor of Linux.  See if it does the same thing.

I'm not the only one who enjoys the benefits of PCLinuxOS then.....

---

### Post by DalgetyDad on 2006-10-18
To Ashrael - 
I opened up the Ubuntu Live 5.10 CD and selected System/Disks. My system froze up before showing any information on the 2 disks which I have fitted (80 GB, WinXP, formatted NTFS and 6GB, now blank).

---

### Post by doobit on 2006-10-18
I had trouble with installing from the live CD on my computer with about the same specs as yours. The alternate install CD is a good solution. Gnome will work fine on it. In fact I have Gnome, KDE, XFce, Windowmaker, and Fluxbox all working great on it. The lighter interfaces are faster, of course, but you can't beat Gnome and KDE for eye candy.

---

### Post by DalgetyDad on 2006-10-18
Further silliness. Running Ubuntu 6.10 Beta from the CD selected GParted. My 6GB disk is not being seen so I tried to resize the partition on the 80GB drive to free up about 20GB for a Ubuntu installation. However the resize failed after about 5 minutes, fortunately without eating the contents of the disk. There must be better ways of passing the time!

---

### Post by DalgetyDad on 2006-10-18
Incidentally, Disk Manager on the Dapper CD freezes up too without displaying any info on the disks. There would appear to be a major compatibility issue here.

---

### Post by DalgetyDad on 2006-10-18
The flush is distinctly busted. I give up.

---

### Post by gn2 on 2006-10-18
> **DalgetyDad said:**
> The flush is distinctly busted. I give up.

In agreement with a previous suggestion i strongly recommend you give PCLinuxOS a try.

In my opinion it's a superior distro. [http://www.pclinuxos.com/page.php?7](http://www.pclinuxos.com/page.php?7)

Go for the full monty "Big Daddy" version, it's the business.

---

### Post by DalgetyDad on 2006-10-18
Downloaded and burned "Big Daddy" and tried an install. You guessed it; system froze up 5 minutes after partitioning and formatting my 6GB hdb. Both Ubuntu and Big Daddy think that they set up hdb as I have specified but back here in the Windows world the Disk Manager shows the disk as being a single Fat32 partition. I'm loath to mess about with hda as with my luck I'll probably write off 15 years of family records. I'll sleep on it and think what to do later.

---

### Post by gn2 on 2006-10-18
Here's my install guide which will safeguard your data: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Have you tried the additional install options, eg "noapic nolapic" to see if that helps?

All of the above applies equally to PCLinuxOS and Ubuntu.

Have you verified the discs you have burned?

---

### Post by Ashrael on 2006-10-20
To DalgetyDad...

sorry to hear about your problems with Ubuntu, my experience is quite different...I'm quite sure there must have been errors on your disks, i had a similar problem this week, the diskmanager hung the entire machine, rebooted xp and tested my drives, and yes, there was an error on there, wich windowsxp couldn't fix :-?  I downloaded some apps and fixed the error, booted Ubuntu again......and no more hanging diskmanager....it turned out that the drive was recognized as ntfs, while it was fat32, windows didn't bother with this error but Ubuntu did....So i hope you haven't formatted your drive too often, for it might be possible to retreive the data you lost....Lesson: back up personal and important data regularly...I went on my face a couple of times too. If there is anything i can do to advise or help, just let me know....

Ashrael.

---

### Post by DalgetyDad on 2006-10-20
To everyone who offered assistance I would like to extend my warmest appreciation. My problems appear to be behind me and I now have a glossy new installation of PCLinuxOS waiting to be explored. I believe that my difficulties in formatting my disks were caused by the fact that when I dropped out of WinXP I was doing it by hibernating rather than shutting down completely. I had got into this habit because it takes so long for windows to come back up, what with loading anti-virus, anti-spyware etc, each of which has to check if there are any updates waiting for them. At least 6 minutes is lost each time windows is re-started from scratch. 
  It would appear that hiberfil.sys was not letting me make any changes to the disks. Anyway, when I did a boot with the live CD from a completely shut down system everything galloped through and I still have my windows unbroken.
  Once again, thanks for the help and support.

---

