---
title: "I can't install 6.10 into Dell"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by surya on 2007-02-01
I'm new in Linux and so on Ubuntu. I have a problem to install ubuntu 6.10 into my PC.
My PC specification:

Dell Optiplex GX280
Pentium 4 HT 3.2GHz
Intel 915 Chipset
1GB DDR2
2x80GB SATA

What I want to do is, I want to make it dual boot. 1st HDD for Windows XP and 2nd is for Ubuntu. The problem is when I reach **step 6 of 7 - Prepare disk space** (if I'm not mistaken). It just only show one option. Manually edit partition table. Then I just click Forward. On the prepare partitions step, there is no device detected. Ubuntu can't detect both of my SATA drive. I already try a lot, nearly 2 week just try to install but failed. I hope I can find the solution here.

Kindly somebody show me how to install... :( 

p/s: Already try using 6.06 LTS, also give same result


...**Help!!!**...

---

### Post by mr.wizrd on 2007-02-01
Disclaimer: I am NOT currently running Ubuntu, I did run 6.06 LTS a while back for a little while. I've been reading the forums for a few days in preparation for purchasing a laptop to run 6.10 on, and I am only offering the following advice because there are others with similar problems which all seem to be fixed with this solution. YMMV, and all that.

Credit for this goes to redsymbol, thread link [http://ubuntuforums.org/showpost.php?p=1782230](http://ubuntuforums.org/showpost.php?p=1782230)

>  
I got it by adding this boot parameter:

**acpi=force irqpoll**

Hit 'F6' at the initial Ubuntu install menu. (i.e., when you boot the CD)
When you press F6, a line of preset boot parameters is shown for you to edit. On further testing, you can just append '**acpi=force irqpoll**' to the end of that line.

You might also try this thread: [http://ubuntuforums.org/showthread.php?t=299802](http://ubuntuforums.org/showthread.php?t=299802). It seems that this is a common problem for SATA drives which was fixed using the **acpi=force irqpoll **parameter. 

Hope this helps :)



Best of luck with Ubuntu!

---

### Post by old_geekster on 2007-02-01
> **surya said:**
> I'm new in Linux and so on Ubuntu. I have a problem to install ubuntu 6.10 into my PC.
My PC specification:

Dell Optiplex GX280
Pentium 4 HT 3.2GHz
Intel 915 Chipset
1GB DDR2
2x80GB SATA

What I want to do is, I want to make it dual boot. 1st HDD for Windows XP and 2nd is for Ubuntu. The problem is when I reach **step 6 of 7 - Prepare disk space** (if I'm not mistaken). It just only show one option. Manually edit partition table. Then I just click Forward. On the prepare partitions step, there is no device detected. Ubuntu can't detect both of my SATA drive. I already try a lot, nearly 2 week just try to install but failed. I hope I can find the solution here.

Kindly somebody show me how to install... :( 

p/s: Already try using 6.06 LTS, also give same result


...**Help!!!**...
I have recently installed Ubuntu Edgy Eft 6.10 at least 7 times on my rig.  This was in a week's time period.  It has worked perfectly each time.  I simply messed it up after it was installed.  So, I re-installed it.  This is the best reason for having it on a second drive.

First, do you have Windows installed on the first drive?  This is where GRUB (GRand Unified Bootoader) will be installed.  GRUB allows you to choose which OS should start at boot.  This should be done before attempting to install Ubuntu Edy Eft 6.10.  Once this is done, assure that your second drive appears in "Disk Management""; Start/right click My Computer/Manage/and Disk Management.  I would leave it all "Free Space".  Ubuntu will help you make the partitions.

When you get to the point that you mention in your post --- do you click the button "Manually Edit the Partition Table" (May not be exact wording)?  If not, you should.  Then, you should see a Gparted (Partitioning app) screen with your Windows HDD on it.  It will show the partitions.  I have two.

There will be a switch (lack of better word) on the right side of the box.  Click it, and you should see the second drive.  Click on the second drive.  This is where you create the partitions.  You would "right click" on the drive and click "New".  Create at least a 10GiB partition for (/).  Once this partition is created, click on the drive again.  This time you will click "New" again and create a "swap" partition of from 1-4GiB.  Last, you click on the drive again and click "New".  This is the remainder of the drive and it will be (/home).

Each time that you make a partition, leave "zero" space before the partition that you create.  This way there will be no Free Space between them.

I hope this isn't too confusing.  Here is a link that should help:

[http://www.debianadmin.com/kubuntu-610-edgy-eft-step-by-step-installation-with-screenshots.html](http://www.debianadmin.com/kubuntu-610-edgy-eft-step-by-step-installation-with-screenshots.html)

Don't be confused by the fact that this says Kubuntu.  Kubuntu is Ubuntu with a KDE desktop, instead of Gnome.  So, everything is basically the same.

You simply have to add the information that is applicable to you and your area of the world.

---

### Post by Ocxic on 2007-02-01
make sure your bios has it's SATA RAID option disabled, that could cause a problem.

---

### Post by Motoxrdude on 2007-02-01
> **mr.wizrd said:**
> Disclaimer: I am NOT currently running Ubuntu, I did run 6.06 LTS a while back for a little while. I've been reading the forums for a few days in preparation for purchasing a laptop to run 6.10 on, and I am only offering the following advice because there are others with similar problems which all seem to be fixed with this solution. YMMV, and all that.

Credit for this goes to redsymbol, thread link [http://ubuntuforums.org/showpost.php?p=1782230](http://ubuntuforums.org/showpost.php?p=1782230)



You might also try this thread: [http://ubuntuforums.org/showthread.php?t=299802](http://ubuntuforums.org/showthread.php?t=299802). It seems that this is a common problem for SATA drives which was fixed using the **acpi=force irqpoll **parameter. 

Hope this helps :)



Best of luck with Ubuntu!

Reread his post. He said that his hdd isn't detected by ubuntu.

---

### Post by surya on 2007-02-02
> **Ocxic said:**
> make sure your bios has it's SATA RAID option disabled, that could cause a problem.

Sorry, not much help here
If you familiar with Dell's BIOS, it didn't show any about SATA Raid Enable/Disable.
By the way, I already update the BIOS with the latest one. Also nothing much different.

...**Sigh**...

---

### Post by surya on 2007-02-02
I'm appreciate with your step by step guide here **old_geekster**
The problem is Gparted didn't show any HDD or any partition.
Both of my SATA drive never show. I'm halted here...

...** :( **...

---

### Post by surya on 2007-02-02
> **mr.wizrd said:**
> Disclaimer: I am NOT currently running Ubuntu, I did run 6.06 LTS a while back for a little while. I've been reading the forums for a few days in preparation for purchasing a laptop to run 6.10 on, and I am only offering the following advice because there are others with similar problems which all seem to be fixed with this solution. YMMV, and all that.

Credit for this goes to redsymbol, thread link [http://ubuntuforums.org/showpost.php?p=1782230](http://ubuntuforums.org/showpost.php?p=1782230)



You might also try this thread: [http://ubuntuforums.org/showthread.php?t=299802](http://ubuntuforums.org/showthread.php?t=299802). It seems that this is a common problem for SATA drives which was fixed using the **acpi=force irqpoll **parameter. 

Hope this helps :)



Best of luck with Ubuntu!

I already try, but nothing happen.
Maybe I have to figure out.

...** :confused: **...

---

### Post by surya on 2007-02-02
At last, I can install Ubuntu in my PC and make it dual boot.
Thanx a lot guys, for helping me out. Very much appreciate

Let me explain what I did
1st I try put **acpi=force irqpoll** parameter at the end of the line like **mr.wizrd** told me.
But nothing happen still Ubuntu can't detect my SATA drive

Then I read thread [http://ubuntuforums.org/showpost.php?p=1782230](http://ubuntuforums.org/showpost.php?p=1782230) that **mr.wizrd** gave me and *wallaa*. I figure out that it work when I put the **acpi=force irqpoll** parameter in between 2nd and 3rd parameter of the line. After that both of my SATA drive appear.

I'm very happy with it. :D 
Thanx again, if not maybe I'm not one of the Ubuntu user

...**New Ubuntu & Linux User**...

---

### Post by mr.wizrd on 2007-02-02
Congratulations, glad we got the problem fixed! Cheers all :D

---

