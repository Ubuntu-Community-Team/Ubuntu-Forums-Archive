---
title: "[SOLVED] How to BACKUP, backup!!! need help - make a full reinstallable DVD iso... HO"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Ubunt2Etudiant2008 on 2008-03-18
Hey guys

just installed Gutsy 7.10, did all the heavy updates, did all medibuntu stuff, added extra apps...etc

now I need a full BACKUP!

i want the backup to be an iso file which i will first save on my external usb hard drive

ok

then i wann burn a DVD copy of that iso, so that i can reinstall ubuntu from it directly

Please tell me how in easy steps, i am a newbee
---

All I want is a full reinstallable / bootable DVD of my current system

so in case of breakage, which is certainly gonna happen, with my

DVD I'm back in action in no time :)

---

### Post by Oldsoldier2003 on 2008-03-18
> **Ubunt2Etudiant2008 said:**
> Hey guys

just installed Gutsy 7.10, did all the heavy updates, did all medibuntu stuff, added extra apps...etc

now I need a full BACKUP!

i want the backup to be an iso file which i will first save on my external usb hard drive

ok

then i wann burn a DVD copy of that iso, so that i can reinstall ubuntu from it directly

Please tell me how in easy steps, i am a newbee
---

All I want is a full reinstallable / bootable DVD of my current system

so in case of breakage, which is certainly gonna happen, with my

DVD I'm back in action in no time :)

try this:
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by coninsan on 2008-03-18
think i am listening on this one, would love to get a good backup myself :)

---

### Post by Ubunt2Etudiant2008 on 2008-03-18
I found this

[http://ubuntuforums.org/showthread.php?t=702832](http://ubuntuforums.org/showthread.php?t=702832)

>  Re: The right way to make a full system backup?
You can use this tool Remastersys!
[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)
Top tool i love it
It will make a FULL System backup of your computer and make a ISO image what you can burn on to a DVD disk, Making a Live CD of your System
Then you can install your computer back anytime by using the disk, How it was with everything on it and back the way it was!

so i will try it

are there any other options, better, faster...?

---

### Post by Duck2006 on 2008-03-18
You can use partimage to back up your system.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by FreewareFan on 2008-03-18
Remastersys is the way to go!  I've used it several times, it is painless, fast, and works each and every time.  It will do EXACTLY what you want..  

Just use the command  "  sudo remastersys backup "  to have it include all your personal files, and you've got it made.

Here is a link to a step-by-step tutorial in using it.  You can't go wrong.... 

  [http://howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

Why wait, go and do it now!

FwF

---

### Post by Ubunt2Etudiant2008 on 2008-03-18
Ok guys, can someone answer this

the 2 hard drives in my ubuntu PC are ancient

one is 8gb the other 6gb

now lets say i make my DVD iso bootable backup and my OS drive goes kaputt

i certainly cant find that drive again in a shop (even if it was available i would get a newer bigger one)

anyhoo, if i put in a new 60gb drive and then try and reinstall from my backup DVD, is that gonna cause problems?

i mean does the hardware system always have to be completely identical for the backup dvd to work?

thanks

---

### Post by Duck2006 on 2008-03-18
> **Ubunt2Etudiant2008 said:**
> Ok guys, can someone answer this

the 2 hard drives in my ubuntu PC are ancient

one is 8gb the other 6gb

now lets say i make my DVD iso bootable backup and my OS drive goes kaputt

i certainly cant find that drive again in a shop (even if it was available i would get a newer bigger one)

anyhoo, if i put in a new 60gb drive and then try and reinstall from my backup DVD, is that gonna cause problems?

i mean does the hardware system always have to be completely identical for the backup dvd to work?

thanks

No the the drive don't have to be the same size.

---

### Post by Ubunt2Etudiant2008 on 2008-03-18
> **Duck2006 said:**
> No the the drive don't have to be the same size.

GREAT!!!

makes life easier :)

---

### Post by FreewareFan on 2008-03-18
Correct, the size of the drive does not matter.  What you are doing when you use remastersys, is actually making your own Live-CD.  It's just like the cd you used to install Ubuntu with the first time you did it, except that this CD or DVD, doesn't matter which one you use, anyway, it will have all your settings, customizations, and personal files on it, and they will all be installed, just as your system is the moment you make the DVD.

I swear, it's exactly what you want.

FwF

---

### Post by backflip on 2008-03-18
> **FreewareFan said:**
> Correct, the size of the drive does not matter.  What you are doing when you use remastersys, is actually making your own Live-CD.  It's just like the cd you used to install Ubuntu with the first time you did it, except that this CD or DVD, doesn't matter which one you use, anyway, it will have all your settings, customizations, and personal files on it, and they will all be installed, just as your system is the moment you make the DVD.

I swear, it's exactly what you want.

FwF

Thanks, I found this post really helpful. I'm presently making my Live-CD and I've a couple of questions.
1) I take it once the image is complete (it is still copying as I write) that I burn the result to dvd as an ISO?
2) My present hard drive has three partitions for root, home and swap. If it breaks and I install a new one on the same system do I need to make the same partitions as I previously had and THEN use the Live-Cd I created or do I just install a brand new HD and the created Live_CD will take care of formatting and setting up new  partitions and if so would it let me install root(or any other partition)  on the partition I choose and not one the process chooses for me.
Thanks.

---

### Post by duncan.hawthorne on 2008-03-18
why not just use copy and paste to back up your home directory, back up your software sources list (/etc/apt/sources.list) save your list of installed packages from synaptic (save markings) for you to import again if something goes wrong

then when something breaks you will have all your programs, all your documents, all your settings, without using an overkill solution, in like 5 clicks.

for example why waste 5gb backing up programs when a couple of kilobytes text file will list all your programs and synaptic can just install them from the repos

---

### Post by FreewareFan on 2008-03-18
> **backflip said:**
> Thanks, I found this post really helpful. I'm presently making my Live-CD and I've a couple of questions.
1) I take it once the image is complete (it is still copying as I write) that I burn the result to dvd as an ISO?
2) My present hard drive has three partitions for root, home and swap. If it breaks and I install a new one on the same system do I need to make the same partitions as I previously had and THEN use the Live-Cd I created or do I just install a brand new HD and the created Live_CD will take care of formatting and setting up new  partitions and if so would it let me install root(or any other partition)  on the partition I choose and not one the process chooses for me.
Thanks.

Glad to have been of help to you!

#1. Yes, when it's done, you'll have an .iso file, and you can burn it to a Cd or if it's too large, then burn it to a DVD.  Just tell your burner program that you want to burn a disk image, and point it to your .iso file, and you're set.

#2. Just as the original Live-Cd will not automatically do the partitioning for you, neither will your custom Live-CD automatically do the partitioning for you either.  You'll have to do that yourself, but it's easy, now that you've gone through it when you first installed Ubuntu, right?  So, if you're using the same HD as previously had Ubuntu on it, then I would delete the partitions, and start from square one.  If you have a new HD, then you will by default have to start from scratch.  

Point of interest... When you have finished burning your .iso, and have tested the result, don't forget to run sudo remastersys clean to free up the space on your drive..

Have fun!

FwF

---

### Post by FreewareFan on 2008-03-18
> **duncan.hawthorne said:**
> why not just use copy and paste to back up your home directory, back up your software sources list (/etc/apt/sources.list) save your list of installed packages from synaptic (save markings) for you to import again if something goes wrong

then when something breaks you will have all your programs, all your documents, all your settings, without using an overkill solution, in like 5 clicks.

for example why waste 5gb backing up programs when a couple of kilobytes text file will list all your programs and synaptic can just install them from the repos

Synaptic will not install your customizations, your favorite wallpaper, your system tweaks, etc.....  There is also the time and effort factor...  You've already spent the time and effort to download, install, set program preferences, all that... Why do it again when it only takes about 30 mins and a DVD to have things just the way you have them now??

FwF

---

### Post by duncan.hawthorne on 2008-03-18
>>> Synaptic will not install your customizations, your favorite wallpaper, your system tweaks, etc..... There is also the time and effort factor... You've already spent the time and effort to download, install, set program preferences, all that... Why do it again when it only takes about 30 mins and a DVD to have things just the way you have them now??


synaptic wont, but backing up your home folder will, all of your user settings, program preferences, wallpaper etc are stored in hidden files in your home directory

if you simply adopt your old home folder on a new install (which takes like 2 seconds) all your old settings are used because they are all stored in home folder.
its really extremely easy, you dont have to reconfigure every program, just adopt your old home directory which can be backed up with something as simple as copy and paste, not the monstrous solutions suggested here

---

### Post by coninsan on 2008-03-18
I have a question about this, it sound really great that you can back up your system with a live-cd.
But.

i know i am not the only one with a semi big harddrive, 160gb, partitioned over 5 partitions, 1 for linux, 2 for its swap and etc. a shared partition and windows xp on the last drive. 

will Remastersys just make a copi and zip it as a backup, which will fill many gb's, or will it make a small and neat cd size package that can acctually fit on a cd, which will install your whole system and all of its files?

---

### Post by MasterJS on 2008-03-18
FreeWareFan mentioned that you could save the list of installed packages. Once you've done that, how do you have synaptic put it back after you've reformatted everything?

---

### Post by backflip on 2008-03-18
> **FreewareFan said:**
> Glad to have been of help to you!

#1. Yes, when it's done, you'll have an .iso file, and you can burn it to a Cd or if it's too large, then burn it to a DVD.  Just tell your burner program that you want to burn a disk image, and point it to your .iso file, and you're set.

#2. Just as the original Live-Cd will not automatically do the partitioning for you, neither will your custom Live-CD automatically do the partitioning for you either.  You'll have to do that yourself, but it's easy, now that you've gone through it when you first installed Ubuntu, right?  So, if you're using the same HD as previously had Ubuntu on it, then I would delete the partitions, and start from square one.  If you have a new HD, then you will by default have to start from scratch.  

Point of interest... When you have finished burning your .iso, and have tested the result, don't forget to run sudo remastersys clean to free up the space on your drive..

Have fun!

FwF


Thank you, I much appreciate your help, you've made this so easy to understand, exactly what I needed.

---

### Post by FreewareFan on 2008-03-18
> **duncan.hawthorne said:**
> >>> 
synaptic wont, but backing up your home folder will, all of your user settings, program preferences, wallpaper etc are stored in hidden files in your home directory

if you simply adopt your old home folder on a new install (which takes like 2 seconds) all your old settings are used because they are all stored in home folder.
its really extremely easy, you dont have to reconfigure every program, just adopt your old home directory which can be backed up with something as simple as copy and paste, not the monstrous solutions suggested here

OK, point taken.  But how about the hours it will take to download, and install, all those programs you already have installed?  I don't see a solution for that in your method.

---

### Post by FreewareFan on 2008-03-18
> **MasterJS said:**
> FreeWareFan mentioned that you could save the list of installed packages. Once you've done that, how do you have synaptic put it back after you've reformatted everything?

Nope, wasn't me that said that.  duncan was the one who said that.  I've never used that feature of Synaptic, so I'm at a loss as to how that would work.  duncan will have to ring in with the answer to that.

---

### Post by FreewareFan on 2008-03-18
> **coninsan said:**
> I have a question about this, it sound really great that you can back up your system with a live-cd.
But.

i know i am not the only one with a semi big harddrive, 160gb, partitioned over 5 partitions, 1 for linux, 2 for its swap and etc. a shared partition and windows xp on the last drive. 

will Remastersys just make a copi and zip it as a backup, which will fill many gb's, or will it make a small and neat cd size package that can acctually fit on a cd, which will install your whole system and all of its files?
 
Remastersys will not make a backup of your Windows partition, nor will it backup your swap partitions, nor your shared partition.  It only makes an image of your linux  partition, and your home directory if you tell it to.  You don't' have to include your home directory if you don't want to. 

The best thing to do is to go to the website of Remastersys, take some time to read all about it, and many of your questions will be answered.

---

### Post by FreewareFan on 2008-03-18
> **backflip said:**
> Thank you, I much appreciate your help, you've made this so easy to understand, exactly what I needed.

You are most welcome!  Glad to have been of service.

---

### Post by Ubunt2Etudiant2008 on 2008-03-18
**Important!!!**

> 
Point of interest... When you have finished burning your .iso, and have tested the result, don't forget to run **_sudo remastersys clean_** to free up the space on your drive..

---

### Post by Ubunt2Etudiant2008 on 2008-03-18
**FreewareFan** was kind enough to point this out

>  Originally Posted by Ubunt2Etudiant2008
[http://ubuntuforums.org/showthread.php?t=727999](http://ubuntuforums.org/showthread.php?t=727999)

thank you for all your help

___

please i still have a question

1: how do i get the gui for remastersys

2: with the command "sudo remastersys backup" it started backing up on the same drive
but its too small

how do i tell it to make the backup on to my external usb drive

thanks
----
reply

**Hey, another thing. Make sure that you have the latest version, because it places a Launcher on your desktop, and from there, you can set things like where to store the .iso file at..**

Have fun!
__________________
To Be Free, Is The Way To Be... 

---

