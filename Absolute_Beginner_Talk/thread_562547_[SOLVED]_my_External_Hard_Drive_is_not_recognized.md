---
title: "[SOLVED] my External Hard Drive is not recognized"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by alcatraz678 on 2007-09-28
I have 250 GB external Hard drive.
Its not working on my computer

It always warns me "Cannot mount volume"
Please help me on this, I just transfered from Windows Vista

Other problems I have is,
Is the Photoshop CS3 and Dreamweaver CS3 working on Ubuntu 7.10?
If so, how to install these 2 'cause I really need those Apps to start working on my projects again.

And is there a way to open a .chm files?

Thanks

---

### Post by Linux_Man on 2007-09-28
Is the external hard drive USB? Or FireWire or which connector. Which is it formated as? EXT3? Swap? FAT16? FAT32?


Oh as for Dreamweaver and Photoshop MAY work on WINE, on any ubuntu version. However the GIMP may help you with photoshop needs

---

### Post by alcatraz678 on 2007-09-28
I assume my hard drive is NTFS because I was working with Windows.
It's connected with USB

---

### Post by alcatraz678 on 2007-09-29
bump

---

### Post by bodhi.zazen on 2007-09-29
Well, hard to say ...

Plug in the drive and post the output of these commands :

```
sudo fdisk -l
mount
```

---

### Post by alcatraz678 on 2007-09-29
here:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00080007

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19507   156689946   83  Linux
/dev/sda2           38160       38913     6056505    5  Extended
/dev/sda3   *       19508       38159   149822190   83  Linux
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris
/dev/sda6           38160       38536     3028189+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by BertP on 2007-09-29
I have no personal experience with this issue (yet) but I would guess if the external hard drive is NTFS then Ubuntu wont be able to read it without a special driver.     I think I recall one such driver is listed in the Misc section of the  Automatix install package.

You can get Automatix at [www.getautomatix.com](www.getautomatix.com),    Run Automatic and go to the misc section to find the NTFS driver you will need to install

    let me know if this works for you.  I myself have backup data on an external hard drive with an NTFS  partition  that I will one day want to access from Ubunto

---

### Post by bodhi.zazen on 2007-09-29
> **BertP said:**
> I have no personal experience with this issue (yet) but I would guess if the external hard drive is NTFS then Ubuntu wont be able to read it without a special driver.     I think I recall one such driver is listed in the Misc section of the  Automatix install package.

You can get Automatix at [www.getautomatix.com](www.getautomatix.com),    Run Automatic and go to the misc section to find the NTFS driver you will need to install

    let me know if this works for you.  I myself have backup data on an external hard drive with an NTFS  partition  that I will one day want to access from Ubunto

Ummm ... no, nice try but, no, no, no

First the hard drive is not being recognized ...

What type of hard drive is it ? Model and make ?

Does is come with the option to connect an external power source, if so plug it in and re-try.

---

### Post by BertP on 2007-09-29
Some Windows apps can be ran under Ubuntu WIne  which you can found with the traditional package installers.   Virtualizers such as VMWare can be found using Automatix

I also noticed GnoCHM is available  in the office section of the Automatix installer

Good Luck

---

### Post by bodhi.zazen on 2007-09-29
> **BertP said:**
> Some Windows apps can be ran under Ubuntu WIne  which you can found with the traditional package installers.   Virtualizers such as VMWare can be found using Automatix

I also noticed GnoCHM is available  in the office section of the Automatix installer

Good Luck

As this is the Ubuntu forums, one should stay to the official supported ubuntu methods.

Automatix has it's own forums and I am sure they could use your help.

However this is the Ubutnu Forums and automatix is not supported here :

[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)

---

### Post by BertP on 2007-09-29
Sorry, didn't mean to step on any toes.      Are there  "official" Ubuntu solutions to the various migration-related problems that alcatraz678 described?  If so, please let me know because I am  
am a newcomer here and still discovering what's available on Ubuntu

---

### Post by BertP on 2007-09-29
Disclaimer:

Automatix is an application I found  doing one of the exercises in "Ubuntu For Non-Geeks" 2nd ed.  by Rickford Grant.    I viewed  the inclusion of Automatix  in Grant's book as an endorsement and, so far, I have not had any problems using Automatix  or  the few programs I have installed using Automatix.

However I just found some information of which  those considering using Automatix  should  be aware:    [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by alcatraz678 on 2007-09-29
> **bodhi.zazen said:**
> Ummm ... no, nice try but, no, no, no

First the hard drive is not being recognized ...

What type of hard drive is it ? Model and make ?

Does is come with the option to connect an external power source, if so plug it in and re-try.

Seagate Barracuda 7200.10 250 Gigabytes
Yah, its an external hard drive for my files.

---

### Post by xaco1234 on 2007-09-29
got the same problem with one of my ntfs partition, every time windows is shuted down wrong it won't work, try to use vista and use remove hardware or somthing similar before you take it out of of usb elle firewire

---

### Post by alcatraz678 on 2007-09-29
> **xaco1234 said:**
> got the same problem with one of my ntfs partition, every time windows is shuted down wrong it won't work, try to use vista and use remove hardware or somthing similar before you take it out of of usb elle firewire

Ok dude, gonna try it in a sec.
Thanks for the suggestion

---

### Post by alcatraz678 on 2007-09-29
Hey, it worked properly.. 
haha
Now I can start working again

---

### Post by bodhi.zazen on 2007-09-29
> **BertP said:**
> Disclaimer:

Automatix is an application I found  doing one of the exercises in "Ubuntu For Non-Geeks" 2nd ed.  by Rickford Grant.    I viewed  the inclusion of Automatix  in Grant's book as an endorsement and, so far, I have not had any problems using Automatix  or  the few programs I have installed using Automatix.

However I just found some information of which  those considering using Automatix  should  be aware:    [http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

Thank you, yes that is the potential problem.

The folks at Automatix are working through that document and developing solutions (again see their forums and the Automatix page in Laucnchpad). As the situation changes the information of the Ubuntu forums will be updated, however there is always a review process involved (like the one you referenced) and those take time. Thus the best source of information re Ax is on their forums.

By using the Ax forums:
1. You will get the most up to date information.
2. You can post bug reports directly with the Ax team.
3. We can keep the flame wars to a minimum.

_To All_: THANK YOU FOR NOT DEGENERATING THIS DISCUSSION INTO AN AUTOMATIX FLAME WAR !!

@alcatraz678 \o/

@xaco1234 Thanks for the advice.

---

