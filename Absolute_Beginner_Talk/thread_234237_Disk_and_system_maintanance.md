---
title: "Disk and system maintanance"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by xhilyn on 2006-08-11
Hi. I appologise in advance if this has been covered elswhere but I searched the Forums and help files but could not find the information I was looking for. I am new to Linux and Ubuntu (which I love) and a complete command line novice and prefer GUI methods of doing things (I'm a Mac OS9 convert) but I dont mind trying the command line if I need to.

I have used Windows 2000 and XP as well as Mac OS 9 and X, in all those systems I have always found the need to use disk tools like Norton Utilities on the PC or TechTool Pro for the Mac to repair the file system and such.

My question is this:

Does Linux and Ubuntu in particular require some thing similar to keep the file sytem and OS working at its best.

I have noticed that Ubuntu checks the disk after every 30 boots, so is that enough or is there a programme or GUI front end or other routines that I need to run to keep the drive and system working at it's best.

Any info would be appreciated. Thanks. Xhi:rolleyes:

---

### Post by robinl on 2006-08-11
Well defrag tools don't even exist in ext3 (there is one for ext2 though). But if you don't mess up your files why do you need to fix them anyways?

---

### Post by GoldBuggie on 2006-08-11
the filesystems in linux ext3, reiserfs etc are better in keeping your fragmentation low then ntfs or fat. so a need for a fragmentation tools hasn't been on everyones priority list. 

ext3 is marginally better then reiserfs when it comes to fragmentation but don't let that stop you from using it. It will take a long time/usage before you will have any benefit from a defrag in linux

---

### Post by xhilyn on 2006-08-11
Hi

Thanks for your replies, but I wasn't really thinking of Defraging drives, as I know that is not really needed in Linux or Mac OSX either.

What I was refering to was Disk Utilities like Norton Disk Doctor and Win Doctor on the PC and TechTool Pro on the Mac.

They both check the OS files and file system and drives for any errors and then fixes them. Which is different to Drive Defragging.

Also on Mac OSX for example there are Daily, Monthly, and Yearly Maintenance tasks that should run themselves in the middle of the night if the Computer is left on or manualy if the computer is swithed off at night.

So I was wondering if Linus and Ubuntu needed to have something  similar done on a regular basis.

Thanks

Xhi:?:

---

### Post by xpod on 2006-08-11
Having spent that fist few months on pc`s with m.e/xp i seemed to spend most of that time hunting down and trying ALL the numerous AV,Ad & spyware that was required in one form or another.Not to mention all the tweakers.

Check this ,check that,scan,defrag,sfc,recover from this ,recover from that...

From the moment i turned on an xp a few months ago till last week when i  got my first iso
ALL i did was scan scan and scan some more.

Aint it great to just type sudo aptitude update AND have your WHOLE sys updated.(ok ok...and upgrade).

The only windows i have to worry about NOW is the ones "she" wants washed

(no app for THAT is there????)Ubunto rocks!!!

sorry THAT`s of no help......dont ubunto tend to itself for all that sort of stuff???

---

### Post by steve.horsley on 2006-08-11
As has been mentioned, Ubuntu does a check every 30 boots. As far as I know this is all that's needed. The check program, if you want to do it by hand, is fsck which is short for file system check.

---

### Post by GoldBuggie on 2006-08-11
if there is a GUI front end for fsch that I do not know. But the check that is done every 30:th mount is sufficiant if not a bit to much. You can read about fsch in the console by doing a "man fsch".

By having fsch checking the filesystem every 30th time you have all the checking you need done automatically. 

I would look into more info about fsch if I were you but it is safe to say that you don't need regular manual filesystem control.



Most maintainace I do is keeping my cache clean and empty. Ohh...for this and a bit more you can check out kleensweep. A very nice GUI app that does the job.

---

### Post by Perfect Storm on 2006-08-11
A
```
sudo apt-get clean
```
is sufficient for cleaning the apt temp (downloaded package through apt-get or synaptic).

Also if you use an application and then uninstall it you might check the hidden files in your home folder as it's here the applications save settings/etc. for that user. Only if you want to delte that files/settings.

Other than that, it's self-maintaining.

---

### Post by xhilyn on 2006-08-11
Hi all

Thanks for all your replies. I had thought that perhaps the automatic file check every 30 boots was enough but I just wanted to check.

I will give kleensweep a look as that sound usefull.

Thanks again.

Xhi.:D

---

### Post by Pathfinder_ on 2006-08-11
[this thread]("http://www.ubuntuforums.org/showthread.php?t=140920&highlight=deborphan") might be usefull

---

