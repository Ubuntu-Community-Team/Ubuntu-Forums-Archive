---
title: "Will reformatting/reinstalling 3-4 times completely earase HD?"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by rcane84 on 2007-12-16
I have reinstalled and reformatted my old PIII machine a number of times, probably 3 installations of Ubuntu, 1 of Damn Small Linux.  Would it be at all possible to recover info left over from when it had Windows 98 on it or is that data safely gone now?

---

### Post by Taboo Mirage on 2007-12-16
I would say for all intents and purposes, it is highly unlikely.

---

### Post by Squizz on 2007-12-16
You could probably recover a small amount of it if you had a lot of money to spare or a PhD in computer forensics and a lot of time on your hands - other than that, I'd say you've got no chance.

---

### Post by seventhc on 2007-12-16
To have a secure wipe, data has to be written over it, not just formatted. and even overwriting 7 times will be able to be recovered if someone really wanted to. (provided that they have the correct tools.)
 I think seahorse has a way to do a format with encryption though.
I'll try to find a link but not sure if I can find it or not. And probably not until tomorrow anyway since I'm about to go to sleep. been sick all day :(
How badly do you need it wiped??

I havent read this but it's about the same thing. give it a look.

[http://ubuntuforums.org/showthread.php?t=151699&highlight=wipe+shred+srm&page=2](http://ubuntuforums.org/showthread.php?t=151699&highlight=wipe+shred+srm&page=2)

---

### Post by thelatinist on 2007-12-16
While it is true that someone with enough money, the right tools, the right knowledge, and--most importantly--enough motivation could recover some of your data, unless you are trying to hide something from the military, an intelligence agency, or certain specially trained police forces, you needn't worry.

If you are really worried, physically destroying your HD is the only sure way of preventing any data recovery.

---

### Post by tgalati4 on 2007-12-16
(Well, we don't want to contribute to your paranoia.  But we'll keep an eye on you.)

The Ultimate Boot CD has some tools that are helpful in preparing a disk, including security wipes and low-level formats.

---

### Post by HermanAB on 2007-12-16
Well, I'm paid good money to be paranoid...

No matter how hard you try, you cannot erase a HDD sufficiently well that the government cannot recover most data from it.  However, for ordinary mortals, your data is good as gone once you have re-installed and reformatted.

Every disk drive has a low level erase function built in, that does a pretty good job at erasing the drive: [http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml) Before selling an old drive on Ebay, *please* use that utility to erase it.
However, even that is not necessarily good enough for military use.

Old military drives are collected and dumped under armed guard into a steel smelter and recycled into a car or a washing machine or something.

Cheers,

Herman

---

### Post by rcane84 on 2007-12-16
What about recovering data from before the last full reformat and fresh installation?  I'm thinking about selling the computer and wonder if it would be easy for someone to get to that stuff, not that there is anything particularly valuable but I'm just curious.

---

### Post by ByteJuggler on 2007-12-16
Download [DBAN]("http://dban.sourceforge.net/"), it will for all intents and purpose not be recoverable.

---

### Post by asmoore82 on 2007-12-16
I'm not sure what the question **is**, but ...

**If** you need to get the data back, you could try a **data-carving** tool like
foremost: [http://foremost.sourceforge.net/](http://foremost.sourceforge.net/) , which is in the Ubuntu Repositories,
but you would probably have much better luck running it from a Live environment:
it is available on the x86 versions of SystemRescueCD here: [http://www.sysresccd.org/](http://www.sysresccd.org/)

**If** you wish to ensure that **no one** **can** get the data back;
the **only** way to be **sure** is to dispose of the Hard Disk Drive in a fire or explosion.

---

### Post by Caffeine_Junky on 2007-12-16
> What about recovering data from before the last full reformat and fresh installation? 
Data from **before** the last format/installation would be very hard to recover.

> I'm thinking about selling the computer and wonder if it would be easy for someone to get to that stuff..

It would not be easy, and may not even be possible for the average PC user to get any Data from the original 98 install.
---------
Ok, as I see it your options are:

1)  Remove the HDD and keep it (re-negotiate the selling price)

2) Use a tool such as _Gparted-liveCD_ or [SystemRescueCd]("http://www.sysresccd.org/Main_Page") to ** over write the entire disk a few times**, ..I would format the Entire Disk to Fat32, then to ext3, and then I would use my "XP install disk" to delete any partitions that are on the HDD and format it to NTFS

> Will reformatting/reinstalling 3-4 times completely earase HD?

...of the Original Win98 install?  ... I would say yes

---

### Post by seventhc on 2007-12-16
why don't you keep the hard drive, there are some awesome magnets in there, then you wont have to worry about the info on there. just destroy the disks and keep the magnets. :)

---

### Post by jflaker on 2007-12-16
ByteJuggler said it......Darik's Boot and Nuke (DBAN) is the option of choice.  Download the ISO and burn the image.........boot from the CD and either do the AutoNuke option or take the higher level Nuke options for better assurance.  The higher the level, the longer it takes.

a 40GB drive takes a little more than an hour to destroy..........once nuked, the drive can be disposed of with confidence your data is gone.

---

### Post by Caffeine_Junky on 2007-12-16
> **jflaker said:**
> ByteJuggler said it......Darik's Boot and Nuke (DBAN) is the option of choice.  Download the ISO and burn the image.........boot from the CD and either do the AutoNuke option or take the higher level Nuke options for better assurance.  The higher the level, the longer it takes.

a 40GB drive takes a little more than an hour to destroy..........once nuked, the drive can be disposed of with confidence your data is gone.

If you want to **Destroy ** the HDD and throw it away then this option is the right one.

Personaly I have not tried this Software yet (DBAN)

(ps: I am going to DL a copy of DBAN and add it to my PC Software Toolbox)

---

### Post by cyclefiend2000 on 2007-12-17
+1 for DBAN.

---

