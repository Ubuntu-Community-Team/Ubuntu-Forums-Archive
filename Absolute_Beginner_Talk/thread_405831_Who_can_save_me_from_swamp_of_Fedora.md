---
title: "Who can save me from swamp of Fedora"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by desiretosee on 2007-04-10
I have installed Fedora Core 6 for several times. After I upgraded, they always show blank screen. All the posible ways of healing dont work. So I tried to install Ubuntu. 
Problem is, Ubuntu does not support cdrom with usb interface. so I always recieve permission denied answer for installation. 
My notebook is an IBM thinkpad R32 2568 B4C with intel p4 mobile, 256M memory, ATI radeon Mobile 16 LY with 32M memory. my mainboard is already broken, so I have no cdrom(mainboard doesnt recognize it) I can only install with usb cdrom. Fedora Core support this kind of input. But Ubuntu not. Seems like I am trapped in Fedora swamp now. Who can take me out of it? 
thank u very much!

---

### Post by Zuuswa on 2007-04-10
I take it you have another computer around somewhere??  If so, and you arent intimidated by some more advanced coding, try this

[https://help.ubuntu.com/6.10/ubuntu/...tall-tftp.html](https://help.ubuntu.com/6.10/ubuntu/...tall-tftp.html)

I found additional information at these sites:
[http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)
[https://help.ubuntu.com/community/In...ect=PXEInstall](https://help.ubuntu.com/community/In...ect=PXEInstall)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#DHCP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#DHCP_Server)

Those are instructions on how to install ubuntu over a network.  It will only install the server, so afterwards you will need to do a sudo apt-get install (x)(k)ubuntu-desktop.  You also need to turn your routers dhcp setting off.

I havent tried this yet, but it seams feasable.  Good luck!

---

### Post by kazuya on 2007-04-10
Sorry about your issue. The culprit I see is the ATI videocard. ATI does not make good drivers for linux. My question, what Ubuntu are you trying to install. Did you get dapper, 6.10, or Feisty. I would recommend Feisty or Edgy as they would have more support before install on all your hardware peripherals than dapper 6.06.

Also what USB CDROM are you using? What is your make of Thinkpad again? I have never used those before. 

Somebody else please help here.

In BIOs make sure your first boot device is USB CDROM or USB DVDROM device>
This way it boots up from your CDROM.

How did you get your Ubuntu CD? Did you burn it yourself? If so did you use only 4x to 8x speed and select ISO for your burn?

If you burn it too fast, it would not boot-up. I have installed Ubuntu especially using external USB CDROM.

---

### Post by desiretosee on 2007-04-10
> **kazuya said:**
>  what Ubuntu are you trying to install. Did you get dapper, 6.10, or Feisty. 
I think my Ubuntu should be Edgy 

> **kazuya said:**
>  Also what USB CDROM are you using? What is your make of Thinkpad again? I have never used those before. 

Infact I use an IDE CDROM for desktop, with an Adapter which switch from IDE to USB. Fedora has this option, that you can choose USB massstorage equipment. The DVDrom is a HP   DVD rw rom. my notebook is quite old one. a product of 2002 IBM R32 2568 B4C. 

> **kazuya said:**
>  In BIOs make sure your first boot device is USB CDROM or USB DVDROM device>

I have so done. The sequence is Cd rom first, removeable device (USB) second, third one is another device, forth one is harddisk.

> **kazuya said:**
> How did you get your Ubuntu CD? Did you burn it yourself? If so did you use only 4x to 8x speed and select ISO for your burn?

I have downloaded form [www.ubuntu.com](www.ubuntu.com) version Ubuntu 6.10 with support to 2008. I burn it with nero under windows XP(desktop computer) I burnt it with 40x speed.

---

### Post by arbulus on 2007-04-10
You should definitely slow down the speed of the CD burn.  I've encountered problems a number of times if I let the ISO burn at max speed. I usually burn at 8x.

---

### Post by desiretosee on 2007-04-10
but even the disk that I ve got from my friend, which is Ubuntu 5.04, an official cd, can also not installed on my computer. I think maybe that is a protect trap of Fedora

---

### Post by kazuya on 2007-04-10
burn at 4x or 8x at most. That should get you going. Ubuntu 5.0.4 may not quite work for USB CDROM install. Also, the CD may be too old or scratched..

I wish you ther best though. I have had similar issues where all I see is a grub> prompt
or grub error message.

My fix, use 4x to burn and check to ensure that the file size matches what the original downloaded ISO file should be?

---

### Post by desiretosee on 2007-04-16
Hi! Kazuya, I got it! 
It is not problem of the disk. It is the problem of my external cdrom. 
Because my external dvdrom is a combination of IDE adapter and a DVD rw ROM(which is HL DT - some number. 
I switch this DVD writer with a DVD ROM,then all the CD and DVD that I burnt function very well. And I get totally beautiful and stable Ubuntu. 6.10 installed. 
Thank you very much being so kind to me!
Thanks a lot to all the kind answerer above for your concern!

---

