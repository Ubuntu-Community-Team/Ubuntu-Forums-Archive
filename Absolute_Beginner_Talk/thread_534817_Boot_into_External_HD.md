---
title: "Boot into External HD"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by MasamuneX on 2007-08-25
Good afternoon all,

I've been perusing the forums here for awhile trying to get a straight answer to some questions but can't seem to find any.  I'm fairly confident in my computing abilities and don't shy away too much from messing with BIOS and other crucial settings.  I currently own a Dell laptop (specs at bottom) and have questions.  So here's my questions that've probably been asked about 1000 times:  

1.) What is the procedure for installing Ubuntu to an external HD?

2.) When I unplug that drive and go places will I still be able to boot into windows?  

3.) My laptop is running the ATI X300 Mobile graphics card.  Will there be display issues with this?

4.) My laptop (as well as desktop) monitor are both widescreen, running 1440x900 and 1680x1050 resolution respectively.  Will there be issues regarding Ubuntu displaying using the entire screen?

As I mentioned earlier, I realize some of these questions must've been asked about 1000 times so I apologize for my newb-ness in advance.  Thank you all so much and I look forward to a response.

_Laptop Specs:_
Dell Inspiron 9300
Intel Centrino Mobile Processor @ 1.7Ghz
512 MB RAM
ATI Radeon X300 Mobile Videocard
80GB internal HD
160 GB external HD

---

### Post by Golyadkin on 2007-08-25
Welcome to the forums! 

1) This guide does exactly what you need: [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)  (Found it using the search "install on external usb" )

2) Yes, if the bootmanager GRUB shows up, just choose Windows. 

3) It will work, but maybe not perfectly in full 3D acceleration. This is a handy guide: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

4) This should work, and on the forums there are patches to solve this if you have any trouble.

---

### Post by MasamuneX on 2007-08-25
Thanks so much for the speedy response!  I read through the guide to install Feisty and they recommend installing from the alternate-install CD.  I just have the regular Live CD.  Will that work as well?

One more thing:  I'm fairly familiar with using Gparted and partitioning but I've never been 100% sure what size partitions I should set.  With the 160GB HD (Really only 150GB usable) I wanted to section off about 60GB's for Ubuntu and use the rest as space to put my extra crap from both OS'es.  Within that 60GB's how should the partitions be set up?

**EDIT**

New questions!  A friend of mine showed me a quick youtube video of Beryl (apparently now known as compiz-fusion).  Given the statistics of my computer, would I be able to comfotably run that?  Or is the aforementioned ATI card going ot get in the way?

---

### Post by MasamuneX on 2007-08-25
Anyone?

---

### Post by Golyadkin on 2007-08-26
Installing from the live cd will work fine if you have 256MB of RAM. 

I would partition like this:

/ partition, about 10GB, for all programs and stuff.
swap partition, twice the size of your RAM memory.
/home partition, the rest, this is where you keep all your personal files.

The X300 won't run Beryl very well, but it might work. You would have to try it out. Open a topic in these forums if you are having trouble.

---

