---
title: "uguntu help"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by highlander1398 on 2006-08-09
ok i see alot of help after u get ubuntu installed but i need help with installer crashing

---

### Post by T700 on 2006-08-09
Please provide some detail, so we can help you:
 
1.  What hardware are you installing to?
 
2.  What version of Ubuntu are you using?
 
3.  Describe EXACTLY what happens and at what stage of the install.
 
The more information you can provide *and* giving your question a descriptive title will help the forum better assist you.
 
Paul

---

### Post by highlander1398 on 2006-08-09
ok im sorry about posting it alot but i seen other getting help and it seemed like no one wanted to talk about this so thank you 
ok i downloaded the iso off the ubuntu site burned 4x i am putting it on a computer that i dont know that much about but heres what i know the motherboard is EP-MVP3G2 Processor is amd k6 512 mb of ram i am using the ubuntu 6.06 iso if u need more info i will try and find more thanx everything goes great till i have to click on install then it runs a few min the says installer crashed .  40 gig hd

---

### Post by highlander1398 on 2006-08-09
this is what i get WARNING this will distroy all data on any partitions that are going to be formatted


the following partitions are going to be formatted 

partition#1 of /dev/hdc as ext3
partition#5 of /dev/hdc as swap

---

### Post by davebgimp on 2006-08-09
> **highlander1398 said:**
> this is what i get WARNING this will distroy all data on any partitions that are going to be formatted


the following partitions are going to be formatted 

partition#1 of /dev/hdc as ext3
partition#5 of /dev/hdc as swap

Are you trying to completely wipe your hard drive and install ubuntu as the sole OS? If so, this is fine, it's just a warning that anything on your computer will be wiped to make room for Ubuntu.

If your trying to set up a dual boot situation with Ubuntu **and** Windows, follow this howto:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by highlander1398 on 2006-08-09
yes i just want ubuntu as the os after eveything has run system restarts then i get this 

booting ubuntu kernel 2.6.15-23-386

root(hd0,0

filesystem type is ext2fs ,partition type 0x83
kernel/boot/vmlinux-2.6.15-23-386 root=/dev/hdc1 ro quiet splash run

initrd /boot/initrd.img2.6.15-23-386

[linux-initrd@0x1f942000,0x6ad43fbytes]

savedfault


boot  

uncompressing linux.....

crc error

system halted 

hope that helps

---

### Post by davebgimp on 2006-08-09
I searched the forums for "crc error" and find references to people having better results re-burning the install disk at a slow speed...say 4x for example.

---

### Post by highlander1398 on 2006-08-09
i did burn it at 4x i have 20 cd's with ubuntu on them and i havent got 1 to work yet lol

---

### Post by halfvolle melk on 2006-08-09
Have you checked if the iso is ok?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by highlander1398 on 2006-08-09
yea thers 2 checksums failed i redownloaded it 4 times from diff places same result every time i even tries diff burner software 
cd burner xp pro and even nero7 even at 1x same thing everytime
whats the diff ubuntu and kubuntu?

---

### Post by davebgimp on 2006-08-09
> **highlander1398 said:**
> yea thers 2 checksums failed i redownloaded it 4 times from diff places same result every time i even tries diff burner software 
cd burner xp pro and even nero7 even at 1x same thing everytime
whats the diff ubuntu and kubuntu?


Try this program for burning ISO files. It's what I've used on windows before with success.

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

Ubuntu and Kubuntu use different desktop environments but have the same repositories and base. Ubuntu uses Gnome and Kubuntu uses KDE.

---

### Post by highlander1398 on 2006-08-09
ok i put the same cd in my laptop and it says no checksums failed whats up ? lol could it be my cd drive?

---

### Post by Jose Solorzano on 2006-08-09
Did you try the option "media check" that is included with de UBUNTU Live CD?

---

### Post by highlander1398 on 2006-08-09
i checked cd for errors on the comp i want ubuntu on it says 2 checksums failed on my laptop it says no checkesums failed

---

### Post by Jose Solorzano on 2006-08-09
Maybe your CD-ROM drive is dirt.  Try to clean (with a CD cleaner). Then try to boot with any windows CD (only to test the drive).  If test pass, try UBUNTU again, if no you need a new CD-ROM drive.

---

### Post by highlander1398 on 2006-08-09
i have tried 3 diff drives 1 cd and 2 dvd drives same thing is there something in the computer that would make that happen? im lost
can i put the hd in another comp install ubuntu on it then put it back in the other comp will it detect the new graphx card and new network card?

---

### Post by halfvolle melk on 2006-08-10
[QUOTE=highlander1398]can i put the hd in another comp install ubuntu on it then put it back in the other comp will it detect the new graphx card and new network card?[/QUOTE]
That should work. I've done it a few times. There were no problem with the different NICs (though in some cases I'll bet there might be). This was done on a server so I don't know about the graphics. You'll probably need to reconfigure X afterwards:
[https://wiki.ubuntu.com/CommonProblemsGraphics?highlight=%28dpkg-reconfigure%29](https://wiki.ubuntu.com/CommonProblemsGraphics?highlight=%28dpkg-reconfigure%29)

---

### Post by forkart on 2006-08-15
> **highlander1398 said:**
> yea thers 2 checksums failed i redownloaded it 4 times from diff places same result every time i even tries diff burner software 
cd burner xp pro and even nero7 even at 1x same thing everytime
whats the diff ubuntu and kubuntu?

You can use magiciso to burn this iso image.It works fine without any problem.
[http://www.magiciso.com/](http://www.magiciso.com/)

---

### Post by jocatoth on 2006-08-17
whats the diff ubuntu and kubuntu?

ubuntu is the distribution of ubuntu set up using the Gnome GUI (graphical user interface) while kubuntu is set up using the KDE GUI

---

### Post by wpshooter on 2006-08-17
> **highlander1398 said:**
> i checked cd for errors on the comp i want ubuntu on it says 2 checksums failed on my laptop it says no checkesums failed

Highlander:

How are you doing the sum check of the CD-Rom ?  Make sure you are using the sum check function that is found on the initial Ubuntu boot screen.

Is your CD drive CD-RW capable ?  If so, get yourself some quality/brand named CD-RW media to burn the Ubuntu ISO image on.  That way you can erase the CD-RW as many times as you want and then reburn the image or use the media for anything else you want.

Also, if you have not done so, you might want to consider getting yourself a good disk drive wiping utility and completely wipe out everything from the computer hard drive that you are trying to install Ubuntu onto.  I would do this first and then try installing Ubuntu from a good CD-RW media ISO image.

Good luck.

---

