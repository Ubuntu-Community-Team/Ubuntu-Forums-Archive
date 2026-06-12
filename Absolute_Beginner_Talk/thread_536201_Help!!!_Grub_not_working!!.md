---
title: "Help!!! Grub not working!!"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Magneticgravity on 2007-08-27
Please Help. installed 7.04 though i fear something went wrong. When i reboot, GRUB dosent work!

It says:


GRUB Loading stage1.5.

GRUB Loading, please wait...
Error 15

_



Please help! I cant get onto my PC!!

---

### Post by Marat Galiev on 2007-08-27
Have you Windows installed on you HDD?

---

### Post by Magneticgravity on 2007-08-27
Yes!

---

### Post by Marat Galiev on 2007-08-27
i know way,boot you Windoze xp cd,and press "R" to enter recovery console.
Then enter "1"(to question about copy of windows).
and enter fixmbr in console.
press "y" and enter.
But ...after this,you can't boot linux!:(because windows loader erase you grub boot record...
After this step,you must reinstall you grub or linux right:)

---

### Post by Magneticgravity on 2007-08-27
So this will erase Ubuntu completely?

Will it format Windows or anything? 

Im using a 45GB part. for Xp. will it remain that way or go back up to the max. HDD space.

Is this the easiest way?

---

### Post by kellemes on 2007-08-27
> **Marat Galiev said:**
> 
After this step,you must reinstall you grub or linux right:)

Using a GNU/Linux livecd that is.. (completing the answer) :)

---

### Post by kellemes on 2007-08-27
> **Magneticgravity said:**
> So this will erase Ubuntu completely?

Will it format Windows or anything? 

Im using a 45GB part. for Xp. will it remain that way or go back up to the max. HDD space.

Is this the easiest way?

It will leave your Windows alone, it will only reinstall the bootloader in the MBR.
The next reboot brings you to Windows. Next boot with livecd and reinstall Grub from there, Grub will probably see Windows and add the kernelline in your bootmenu.

---

### Post by Magneticgravity on 2007-08-27
So, i will need the LiveCD again if i wish to install Ubuntu again?

Are you sure this will work?

---

### Post by kellemes on 2007-08-27
> **Magneticgravity said:**
> So, i will need the LiveCD again if i wish to install Ubuntu again?

Are you sure this will work?

You need the LiveCD to get Grub back as your bootloader, and so to be able to startup your installed Ubuntu-system

And yes, it will work, the recoveryconsole on your XP-cd will simply install the XP-bootloader so you can at least startup Windows.
Byt the way, when you're in recoveryconsole you can also type **help** for more info.
But **fixmbr** will probably do the job.

---

### Post by Marat Galiev on 2007-08-27
yes.
fixmbr command ONLY erase you MBR and install windows bootloader.
you ubuntu and windows partitions will safe.
But you must reinstall ubuntu from live cd again.
To install ubuntu,you must format you old linux partitions.
and erase all data from it:)

---

### Post by Magneticgravity on 2007-08-27
OK, thx alot guys, i just get worried if my PC wont start up. Im doing what you said now...

---

### Post by Magneticgravity on 2007-08-27
Guys thanks alot, its the people here who make this forum a very helpful place :D

Im on Xp now, so i should reboot my PC now with the Ubuntu Live CD in the drive?

---

### Post by kellemes on 2007-08-27
> **Magneticgravity said:**
> Guys thanks alot, its the people here who make this forum a very helpful place :D

Im on Xp now, so i should reboot my PC now with the Ubuntu Live CD in the drive?

Yep, you can now reinstall Ubuntu if that's your wish..

---

### Post by Magneticgravity on 2007-08-27
OK, yes i do, so are my partitions still available (the Ubuntu ones)??

---

### Post by fallencyi on 2007-08-27
> **Magneticgravity said:**
> OK, yes i do, so are my partitions still available (the Ubuntu ones)??

Before you do anything  I suggest that you  Backup your important stuff from your working windows os.

Then:

Based on what you've said so far, your existing Ubuntu Partitions should be fine. Windows just hosed your MBR (It has a nasty habit of thinking it's the ONLY OS on a disk).

  You probably do not need to reinstall ubuntu. You should just fix your grub boot menu & place Grub back in  the MBR.

The following Thread Worked for me:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Also Check out google for "Supergrub CD" several people here recommend it.

---

### Post by Magneticgravity on 2007-08-27
Thank you for writing back, but the deed is done - and im happy!

I formatted the Linux Partitions, leaving the Xp ones be, and it worked. Xp runs fine.

I then simply installed Feisty again on LiveCD and now its installed, along with Xp, no problems :D

---

### Post by kellemes on 2007-08-27
Well done! :)

---

