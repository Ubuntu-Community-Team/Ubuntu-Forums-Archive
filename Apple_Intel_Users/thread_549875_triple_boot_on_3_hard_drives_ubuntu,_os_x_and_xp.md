---
title: "triple boot on 3 hard drives ubuntu, os x and xp"
date: 2007-09-13
forum: Apple Intel Users
---

### Post by enilk on 2007-09-13
I have an intel mini mac 1.83 ghz

Osx tiger 10.4 with latest updates
Windows xp sp2 
Ubuntu 7.04

internal mini mac hard drive 80 gig
external firewire/usb drive 150 gig
external firewire/usb 3 gb

i d like to put windows xp on the internal hard drive in the mini, osx on ther 150 gig and ubuntu on the 3 gb
 im trying to use rEFit as my boot loader. Im having problems with the grub saying hardware error i think the grub installer got corrupted when i tried to change it to rEFit ( i installed rEFIT after i went ahead and se up ubuntu on the 3gb drive .. i tried reinstalling it but no dice.:confused:

my ideal setup is 
xp on internal 80 gig
 split external 150 gb into 75gb  for osx the other 75 gig fat 32 for data that can be transfered across all 3 os
ubuntu on 3gb

would like this o have a quint booting system osx tiger osx leopard , xp pro , vista, and ubuntu:popcorn:

any ideas how i can achieve this

would like all oses on seperate hard drives if possible i dont have a TB hard drive just laying around :)

here is my partion info as from partion inspector in rEFit ingoe the fact that my internal has osx and xp on it right now i d really like osx to be on the external since i use os x most of the time and its on a 7200 rpm firewire drive verus a 5400 rpm internal.

Thanks for any ideas 


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     98975783  Mac OS X HFS+
 3       99237928    156301447  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     98975783  af  Mac OS X HFS+
 3 *     99237928    156301447  0c  FAT32 (LBA)

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 99237928:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0c  FAT32 (LBA), active

---

### Post by cyberdork33 on 2007-09-13
People have not had luck booting legacy OSs from external hard drives. Because of the BIOS emulation, your bootable legacy OS partitions need to be one of the first 4 on your main hard disk. For Ubuntu you can make your /boot partition on the main drive (~100MB) and then the normal root partition on the external drive (or anywhere else for that matter). You will probably want a little more space than 3GB for your install anyway as that will likely be a squeeze if you plan on installing anything.

As for getting more that a triple boot setup, good luck, as there is not anyone here that is doing that that I know of. Remeber though that OSX (both Tiger and Leopard) can boot from anywhere on the disk (partitions > 4) since they boot directly from EFI.


BTW, if you are making a shared FAT32 partition for file sharing, why are you making the Windows and OSX partitions so huge? 20GB for each is more than enough if you plan to store personal files on another partition.

---

### Post by enilk on 2007-09-28
Update on this.. Not much to say except i ve got another 20 gig hard drive to try and puit ubuntu on. maybe i can get it all working under grub ??  i have copies of xp pro and xp media center, osx tiger and os x leopard and ubuntu i d like them to work if i cannot get a single boot screen thats ok. I saw a youtube video of quadbooting and it was impressive but no ubuntu. Will hunt up the link in a bit. id prefer keep all os on seprate hard drives but i ll use my 80 gb i nternal for the formatting if need to be and create a data partion but h ow do i do that for my applications i have tons of software and games i want to install on osx and xp and will want to play quake etc on ubuntu to see what the gaming experience is like.

I might try this process 
[http://forum.onmac.net/showthread.php?t=2793](http://forum.onmac.net/showthread.php?t=2793)

---

### Post by cyberdork33 on 2007-09-28
> **enilk said:**
> I might try this process 
[http://forum.onmac.net/showthread.php?t=2793](http://forum.onmac.net/showthread.php?t=2793)

I don't quite understand how he is booting Ubuntu from beyond the 4th partition, but if it works, it works.

---

### Post by ivesjd on 2007-09-29
From what I've seen, rEFIt is your friend. When ever I have external drives pluged in that have a OS on them, I'm able to boot from them.  For example, I have a 60 GB usb drive that used to be my internal laptop drive. When I first took it out I was still able to boot all three OS's that I had on it. If you haven't, I would try to see what rEFIt will do.

---

### Post by enilk on 2007-10-11
I got the 7.10 dvd image and attempted to install it on the 20 gb external via usb the installer saw it just fine , The partoner ran without any problems. When I went into rEFit It shows ubuntu as a legancy windows os icon. when i click on it it hangs wont boot. I have osx and xp on the internal right now via bootcamp. rEFit sees it all just fine just hangs upon booting into ubuntu

---

### Post by cyberdork33 on 2007-10-11
> **enilk said:**
> I got the 7.10 dvd image and attempted to install it on the 20 gb external via usb the installer saw it just fine , The partoner ran without any problems. When I went into rEFit It shows ubuntu as a legancy windows os icon. when i click on it it hangs wont boot. I have osx and xp on the internal right now via bootcamp. rEFit sees it all just fine just hangs upon booting into ubuntu Sounds like the same issue most are having when installing to an external device. You can look here for some progress in this area: [http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)

---

### Post by enilk on 2007-10-11
Thanks for that link i have ubuntu 7.10 installed yay
 my first ever linux installation that was a sucess getting online!!
 Running off the usb via reEFit  i guess i was unable to get it running under refit if it was connected via  firewire. i tried the fire wire due higher speeds  ( this hard drive is a combo of usb and firewire) usb is painfully slow. Now for the interesting thing i took off my boot camp partion just dual boot Ubuntu and osx.. works great.. my next challenge is get xp on an external anybody know where i can update all the hot fixes and sys drivers at once instead of manually i m going to make an unattended cd using nlite hopefully that ll allow me do the usb drive hack. i dream of having a mini with several hard drives connected to it all housing their own os independent from each other except on the internal where the boot loader exists, Give me a heads up if u discover any fire wire based solutions,

Im going to try the windows xp on external and leopard on external whille i count the days till i can afford ultimate vista and leopard drops and i get my new mac book hopefully! i may just try do this guy billbear did quad booting on a single hard drive but figure out how to do it via usb firewiore i know a lot of people will love the idea of seperate os on seperate hds under one bootloader will post link shortly since im on my new gusty instalaltion all my bookmarks r on the other hard drive


PS I have a problem with bluetooth?? hjad to use usb keyboard and wheni click the boothtooth iceon ( made i visble all times) and make it discoverable it sees my mouse and keyboard both apple and when i click connect it spits out this error code??

i updated all 419 upodates the updater found;. I m pretty noobish at this so thanks !

---

