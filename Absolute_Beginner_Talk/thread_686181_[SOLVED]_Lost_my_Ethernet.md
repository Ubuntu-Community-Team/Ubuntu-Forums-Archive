---
title: "[SOLVED] Lost my Ethernet"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by john3347 on 2008-02-03
I finally was able (thanks to advice and links provided by members here) to get Ubuntu 7.10 installed on a second hard drive installed specifically for Ubuntu.  Now a new problem!  I have lost my network connection.  I had normal DSL internet connection through an ethernet router prior to installing Ububnu.  I had no internet connection whit Ubuntu from the start and now I don't have any internet connection with that computer in Windows or Ubuntu.  The computer no longer recognizes the presence of an NIC card in Windows or Ubuntu.  I still have normal internet connection on other computers, some ethernet and some wireless.  Problem only on the one machine.

Anybody got any suggestions?

Thank you.   John

---

### Post by fiddledd on 2008-02-03
> **john3347 said:**
> I finally was able (thanks to advice and links provided by members here) to get Ubuntu 7.10 installed on a second hard drive installed specifically for Ubuntu.  Now a new problem!  I have lost my network connection.  I had normal DSL internet connection through an ethernet router prior to installing Ububnu.  I had no internet connection whit Ubuntu from the start and now I don't have any internet connection with that computer in Windows or Ubuntu.  The computer no longer recognizes the presence of an NIC card in Windows or Ubuntu.  I still have normal internet connection on other computers, some ethernet and some wireless.  Problem only on the one machine.

Anybody got any suggestions?

Thank you.   John

If it is the same on all OS's then it's gotta be a Hardware problem. Just a guess but you say installed Ubuntu on a second HDD, if you added this to your PC you may have knocked the NIC so you could try removing it and reseating it in it's slot. But first check it shows up in the BIOS. If that doesn't work you could remove the second drive (assuming it wasn't installed in your PC before) and see if windows sees your NIC. Failing that you could swap the NIC with one you know is OK (from your other PCs) or buy a new one, they are pretty cheap.

---

### Post by john3347 on 2008-02-04
The NIC is not an actual PCI card, it is on the motherboard.  Perhaps something is wrong in connection with the installation of the second hard drive.  I have re-installed all the drivers with the driver install disc that came with the motherboard and it has had no effect.  The computer is self-built almost exactly a year ago and has been functioning normally up to now.  I guess that it is possible that coincidence caused a NIC failure at this time, too.  Maybe I will try to install a PCI card and see what happens.  I agree that it appears to be a hardware issue rather than a software issue.

---

### Post by john3347 on 2008-02-04
I really want to thank you people here for all the help you are giving me.  I am being able to take your advice and make a litle bit of progress each time you give me a few more guidelines to follow to get things done.  I am finally writing this from within Firefox on Ubuntu.  

Well, I was unable to connect to the internet with this comp\uter after I installed ubuntu, but I didn't have all the details.  I am still having problems, but I have more information. 

If I close Ubuntu and restart without unplugging the computer for a few minutes, it does not recognize the NIC.  (error message states "no connection to internet" or words to that effect).  If I disconnect power for a few minutes and then boot-up, it starts and connects normally. 

I am on a computer with onboard ethernet and Windows XP on a 160 GB hard drive and Ubuntu 7.10 on a second 80GB hard drive.

Anyone got a remedy to this issue?  I got dozens more problems, but I am simple minded enough that I can only attack one at a time.  

Thank you   John

---

### Post by john3347 on 2008-02-16
Well, to update this problem and define whether it is related to Ubuntu or not:  I disconnected the second hard drive (which had been formatted and partitioned prior to installing Ubuntu) and still had no internet.  I formatted C drive and reinstalled Windows XP (with the second drive still disconnected.) and internet returned to normal.  I reconnected the Ubuntu drive and lost internet again.  Again, I had to format and reinstall Windows to return internet.    ( I don't doubt that there would have been a more simple way to return internet after disconnecting the Ububtu drive, but I just didn't know a better way.) 

I would appreciate any suggestions here because I really would like to get a working instance of a Linux OS.  Perhaps a version other than Ubuntu would be better for a new beginner????

---

### Post by john3347 on 2008-02-26
Well, I've given up!! Ubuntu isn't for me.  I used DOS 3 a bit, but it didn't present the problems and frustrations that Ubuntu has presented.  Back to M$ for me I guess.  At least I get answers on technet.  Ubuntu is just not ready for the person who wants to use their computer FOR a project rather than AS a project.

---

