---
title: "problems with windows boot actually (hoping for help here anyway)"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by mixmaster87 on 2007-01-01
i have been an ubuntu user for about a month now. i HAD to get rid of windows so didnt hesitate to remove windows completely, as i heard people said you could do the same things with linux as you could with windows (this is not whine, just opinions and to show how irritating things are for me atm) well, im a gamer, and didnt knew that linux couldnt run games properly, tried to run wow but wouldnt work on me with wine, dont want to pay for cedega, as wine didnt work. and then i decided to go back to windows, in dual booting. so... as i hate windows as mutch as i do, and dont have a windows disk anymore, i downloaded it, several versions, on several burning methods, but the installation stalls at random places no matter what. i burned the iso's at x4 (as it was the slowest i could burn it to) and still hard time installing..

but after 3-4 days of downloading, burning, install and failure, i actually got it to work... now, everytime i start windows, it says "NTLDR is missing, press ctrl, alt, del to restart"... until now i had just put the windows installation disk in to start up and it would load normally, but now some hours ago, my computer froze completely, and booting with the windows disk inside wont work! and if i try to boot from disk only, it says "BOOT FAILURE, PLEASE INSERT WINDOWS DISK" etc... windows have been a complete pain in the *** past 2 years and im totally sick of it! but i "need" to have it cause id like to play games... and then it wont work no matter what i try to do. isnt bill gates one of the richest people in the world? why does HE need to be the only one to be able to earn money on computer gamers!??

written too mutch already, cuestion is:
does any of you know how i can fix that pain in the *** NTLDR file? is my cd rom destroyed or something? (as even some disks wont be read by my cd rom, only in windows though, in linux it reads everything..) i have been totally unabled to use my computer as i used to for 2 moths! i neeeed help..:( i do anything, exept pay a penny to gates....

thx in advantage, anything at all is greatly apresiated!

---

### Post by gn2 on 2007-01-01
Super Grub Disk has a Windows boot facility.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by jonathan.lees on 2007-01-01
Here's a guide I wrote for a college assignment recently about fixing the NTLDR is missing problem:

NTLDR is a program that is loaded from the hard drive boot sector and it displays the Windows start-up menu and also helps Windows to load.

Microsoft ([http://support.microsoft.com/default.aspx?kbid=320397](http://support.microsoft.com/default.aspx?kbid=320397)) states that &#8220;after you copy many files to the root folder of a boot volume that uses the NTFS file system; you may receive the following error message the next time that you restart the computer:

To resolve this problem follow these steps:

1. Insert the Windows XP bootable CD into the computer.
2. When prompted to press any key to boot from the CD, press any key.
3. Once in the Windows XP setup menu press the "R" key to repair Windows and enter the recovery console.
4. Log into your Windows installation by pressing the "1" key and pressing enter, you will then be prompted for the administrator password.
5. Copy the ntldr and ntdetect files from the CD to the root  directory of the primary hard disk. In the below example I copy these files from the CD-ROM drive letter "E". This letter may be different on your computer.
```

copy e:\i386\ntldr c:\
copy e:\i386\ntdetect.com c:\

```
6. Once both of these files have been successfully copied, remove the CD from the computer and reboot.

---

### Post by mixmaster87 on 2007-01-01
btw, im running linux on a 80gb disk, and installed windows again later than linux on another disk (250gb) so they are running on different disk drives, but il try to figure it out with the information i got, thx:D

and as i said, i couldnt load the windows disk, it said boot failure, but i will try the repair thing if i get it going!

and what i did to boot windows instead of linux was just to change the cables for the disks, and leave the windows disk out as i used linux and visa versa*

---

### Post by gn2 on 2007-01-01
In that case, this may interest you: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

