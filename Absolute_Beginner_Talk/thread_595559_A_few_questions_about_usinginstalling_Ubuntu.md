---
title: "A few questions about using/installing Ubuntu"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Todeskatze on 2007-10-28
Well, I am currently downloading the OS as we speak..From a couple of forums I've seen some great performance with this.so, I have a few questins.

1. Am I able to do multiple partitions on the same HDD. (I.E. Can I install, Windows XP and Ubuntu and have them seperate HDD)

2. I've seen a series of programs that allow Ubuntu to run World of Warcraft with a great deal of FPS.
So, where can I get a thread/list of programs to allow the use of World of Warcraft. 

I will add more questions as responses come in.

---

### Post by siciliancasanova on 2007-10-28
To answer question 1:  Yes.  I would suggest downloading and using gParted.  Ubuntu comes with it's own partitioning set up but I have always found it easier and to have more control and just as a great utility to have gParted on a separate cd to create your partitions before you install Ubuntu.

[psychocats.net]("http://www.psychocats.net") has a good visualization of partitions.

I have 100gb for Windows 2gb for Swap, 20gb for my installation and 70 some gigs for my /home folder

---

### Post by Todeskatze on 2007-10-28
> **siciliancasanova said:**
> To answer question 1:  Yes.  I would suggest downloading and using gParted.  Ubuntu comes with it's own partitioning set up but I have always found it easier and to have more control and just as a great utility to have gParted on a separate cd to create your partitions before you install Ubuntu.

[psychocats.net]("http://www.psychocats.net") has a good visualization of partitions.

I have 100gb for Windows 2gb for Swap, 20gb for my installation and 70 some gigs for my /home folder

Thanks for the link, I will be sure to bookmark and read.
Another question I forgot to ask, that I should have when I made this thread.
Will my computer's specs be suitable for Ubuntu?

1.8 Ghz AMD Sempron Processor
256MB NVIDIA GeForce 5500FX
1.25GB RAM
104GB HDD
CD-RW/DVD-ROM Drive
And 6MBPS Cable Internet

Also, will I have to reinstall multiple drivers?

---

### Post by alwiap on 2007-10-28
[http://ubuntuforums.org/showthread.php?t=579378&highlight=world+of+warcraft](http://ubuntuforums.org/showthread.php?t=579378&highlight=world+of+warcraft)

i would imagine you would be fine hardware-wise

---

### Post by pieisgood4589 on 2007-10-28
Right now, you have an absolute minimal system for installing Ubuntu. It will install, but might seem a little sluggish. I would recommend upping the RAM to at least 512 mb. I went RAM crazy and upgraded to 4gigs, and now my computer boots up in like 7 seconds. :lolflag:

---

### Post by siciliancasanova on 2007-10-28
Yeah that's plenty for Ubuntu and you should be able to run most of the features of compiz-fusion fairly painlessly with your set up.

---

### Post by Todeskatze on 2007-10-28
> **pieisgood4589 said:**
> Right now, you have an absolute minimal system for installing Ubuntu. It will install, but might seem a little sluggish. I would recommend upping the RAM to at least 512 mb. I went RAM crazy and upgraded to 4gigs, and now my computer boots up in like 7 seconds. :lolflag:

I do have more than 512MB of Ram, I have 1.25GB as mentioned before.
Lol, I think you got my Video Card's Memory mixed up with ram. XD

---

### Post by mdpalow on 2007-10-29
you don't need to dl anything to partition the drive. The Live Disk will let you partition during install.

Consider this a MANUAL partition option, which you can select when asked:

/                EXT3 File format (10 gigs)
/home        EXT3 file format (87 gigs)
/Windows    FAT 32 file format (5 gigs)
/swap         2 gigs

swap is good at twice your ram size.
separate /home partition is good for backups later.

Your system is fine. I have the same graphics card. Be sure to let RESTRICTED DRIVERS be installed at the end of the install process and make sure you have a CAT5 cable plugged in for Internet during install.

This will be the quickest install you've ever done with an OS. :) Everything will be loaded for you when you're done and you won't have to install anything, but the 9 or so updates - which take less than a minute. After you accept the partition setting you want, you'll be up and running in less than 25 minutes. You'll spend more time getting your desktop to look like you want then it takes to install this OS.

Have fun and good luck,

---

### Post by daengbo on 2007-10-29
> **pieisgood4589 said:**
> Right now, you have an absolute minimal system for installing Ubuntu. It will install, but might seem a little sluggish. I would recommend upping the RAM to at least 512 mb. I went RAM crazy and upgraded to 4gigs, and now my computer boots up in like 7 seconds. :lolflag:

His Graphics RAM is 256GB. His system RAM is 1.25GB

On to the point of WoW.

Make sure you have the NVidia driver installed and disable desktop effects because they can get in the way of OpenGL programs which run full-screen.

I think the easiest way to get this up for you is to use Wine-Doors. It will install all the necessary applications and libraries for you. 
[http://www.wine-doors.org/](http://www.wine-doors.org/)
Download and install the Ubuntu package,

Start the program in Applications -> System Tools and ask to install WoW. Insert your media when requested.

Cheers

---

### Post by Todeskatze on 2007-10-29
Thank you guys for all of your assistance, I will get to working on installing and setting up later tonight, I've bookmarked this thread, and all helpful links mentioned in this thread.

Again, thanks guys for the help, look forward to getting started. :D

---

