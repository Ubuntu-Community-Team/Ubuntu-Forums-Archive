---
title: "[SOLVED] Installing Ubuntu"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2007-10-16
Hey everyone

I just recieved my Ubuntu 7.04 install disc in the mail.  I want to dual boot windows XP and Ubuntu.

I have a question.

When they say to 'back up your files' before you install the OS - which files do I back up?

Other than that I think this gude can help me through pretty well:

[Installation Guide]("http://news.softpedia.com/news/How-to-Install-Ubuntu-7-04-Windows-User-P-O-V-52973.shtml").

Can you think of anything to add?

Thanks for your time,
Steve

---

### Post by LowSky on 2007-10-16
back up all the files you may not want to loose.

Pictures, MP3, photos...documents... whatever.

Remember to defrag you hard drive in Windows before partitioning your hard drive

---

### Post by jpittack on 2007-10-16
Any important documents.  I back up Document and Settings folder in xp.  program that can be replaced are not as important.

---

### Post by Dr Small on 2007-10-16
Backing up your files, means all of you important ones, such as pictures, music, documents, and stuff like that, incase either you accidentally erase the entire drive, and lose your windows, or incase Ubuntu somehow messes up (which is rare.)

Dr Small

---

### Post by AnLGP on 2007-10-16
Thanks.  

My next question is this:

I have my windows boot CD but I don't have the product key.  Is there anything I can do besides backing up my files and crossing my fingers?

---

### Post by pancakelizard on 2007-10-16
> **AnLGP said:**
> Thanks.  

My next question is this:

I have my windows boot CD but I don't have the product key.  Is there anything I can do besides backing up my files and crossing my fingers?

I'm going to assume your product key is valid.
Google for a Windows XP Product scanner or something to that effect.

It will scan your registry for your product key and display it so you can write it down.

---

### Post by LowSky on 2007-10-16
Did XP come with the computer, if its a desktop it will be on the box or inside the case if its a laptop it will be on the bottom.

---

### Post by js_fr on 2007-10-16
I would do a complete backup of your Windows partition(s) with Tools like Acronis Trueimage (under Windows) or Partimage (under Linux). Then - in case you destroy by accident your Windows partition during Linux installation - you can simply restore it using the same Tool and don't have to do a complete new install of Windows.
Partimage which comes e.g. with SystemRescueCD - [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) - and also does backups of NTFS partitions.

---

### Post by AnLGP on 2007-10-16
Yes:

My product is valid.  XP came with the computer.  Thanks for your tips I'll do all of these before I try to install Ubuntu.  I look forward to seeing you on the other side.

By the by I've been running Wubi and it's been pretty interesting thusfar.  I look forward to making it a dedicated partition!  Thanks!

---

### Post by AnLGP on 2007-10-17
I wanted to let everyone know that the install went well.  Thanks for your help.

---

### Post by AnLGP on 2007-10-18
Mistake:

Ubuntu boots fine but when I try and boot into XP it says to put my "System Recovery" CD into the drive.  I did that and selected "Install with backup" option and restart.  The same screen comes up.  What do I do?

---

### Post by AnLGP on 2007-10-19
Also -

I have 200 some Gigs on this computer and this partition only sees about 80.  That really sucks.  Any help would be appreciated.  If there's anything I can do to help you understand more of what's going on let me know.

Steve

---

### Post by mikeize on 2007-10-19
you can try the "super grub disk" (google for it).  put it on a floppy, and try some of the options like "restore windows boot".  Also, you should be able to see all of your partitions from ubuntu...  make sure you have all the updates, especially that you have ntfs read/write support.  I had a lot of trouble getting my dual boot set up right, but messing around with the "super grub disk" helped a lot, if I remember correctly.  

-mike

---

