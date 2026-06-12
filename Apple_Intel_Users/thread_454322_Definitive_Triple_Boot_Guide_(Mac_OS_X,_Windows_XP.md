---
title: "Definitive Triple Boot Guide (Mac OS X, Windows XP, Ubuntu 7.10)"
date: 2007-05-25
forum: Apple Intel Users
---

### Post by RockFromDot on 2007-05-25
I've searched through these forums and around the internet, but I haven't been able to find a definitive guide to attempt to install Ubuntu for someone in my situation.

I have a 2.16 GHz Macbook Pro Core 2 Duo with Mac OS X 10.4.9 and Windows XP SP2 already installed on a 120 GB drive with 80  GB for OS X and 32 GB for XP. I want to add in Ubuntu 7.04 to the already dual boot environment.

I've seen some tutorials for dual booting Mac OS X and 7.04, and triple boot with OS X, XP, and Ubuntu 6.10 but nothing for triple booting OSX, XP, and Ubuntu 7.04. Is there a post on how to go through this process either in these forums or elsewhere?

If need be, I have no issues with re-formatting the XP partition to add space for Ubuntu, but would prefer to keep the OS X install intact...

If there are no such tutorials out there, I don't mind putting one together, but figured I'd ask to see if such a resource already exists...

Thanks...

---

### Post by mrmcd on 2007-05-25
Triple booting with 6.06 or 7.10 shouldn't make a difference .... why not post the guides you saw for triple booting with 6.06 and it can be checked if that guide will work alright by swapping in 7.07?

---

### Post by RockFromDot on 2007-05-25
Well I've found there's a multitude of tutorials out there on how to triple boot, just not one with detailed step by step process on how (and why) to go through my setup. I'm pulling this information from these sites:

[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)
[http://ubuntuforums.org/showthread.php?t=447230](http://ubuntuforums.org/showthread.php?t=447230)
[http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453)
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)
[http://forum.insanelymac.com/index.php?showtopic=46779](http://forum.insanelymac.com/index.php?showtopic=46779)
[http://modular.math.washington.edu/macbook/triboot/](http://modular.math.washington.edu/macbook/triboot/)

I've downloaded the 64-bit version of Ubuntu 7.04 (the non-alternate disto), and already have Windows XP installed along with OSX.

From what I gather I should:

1) Install rEFIt. Can I install this now, without causing any issues since I already have XP installed. Or should I uninstall XP and start from scratch? I don't mind re-formatting and re-partitioning the XP install since I only have OpenOffice, MS Excel 07, and a few demos installed...

2) Partition my drive:

Now I already have 80 GB devoted to OS X and the rest to XP, which is formated NTFS. The only reason I'm keeping XP is for very occasional Excel usage (in other words, only when OpenOffice won't cut it, e.g. when I need to install plug-ins that don't have OO.org versions) and occasional gaming, so I don't really need to write to XP. Should I keep NFTS or switch to FAT32? Any reason for using FAT32 if I don't need to write to XP?

Also, if I resize my OS X partition, will I lose my OS X install, or is OS X smart enough to only partition out free space?

So I know to partition my drive, I'll use:

sudo diskutil resizeVolume disk0s2 XXG Linux Linux XXG "MS-DOS FAT32" Windows XXG

Now, if I just leave the OS X partition at 80GB, do I need to put that into the command, or just leave it blank and it will then leave the OSX partition alone?

3) Install Ubuntu using instructions at [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro). Those instructions seem detailed enough for me, so if I can get through these first two steps I should be all set....

So, basically my questions come down to, can I install rEFIt and re-partition my drives without losing the OS X install and XP install? If I can't re-partition OS X without losing the install (e.g. making the 80 GB into a 40-60 GB partition, while keeping everything that's there), then I might just get rid of XP and give WINE a shot or some other method of running XP through Ubuntu...

---

### Post by MacSolidWorks on 2007-05-25
You can see my post on the Apple forums in order to triple boot:

Ubuntu 7.04 64bit edition
Windows XP  64bit edition
Mac OS X

[http://discussions.apple.com/thread.jspa?threadID=963685](http://discussions.apple.com/thread.jspa?threadID=963685)

-MacSolidWorks

---

### Post by speedemonV12 on 2007-05-28
I was also having the same problem.... I dont think that this person is having trouble with how to install these things, I think that the main problem is that he already has OS X installed, and he already has Windows installed via bootcamp. The thing that he woud like to know, is if it is possible to have both of these installed, and then add another partition for Ubuntu. I would also like to know if this is possible, and then if it is, how do i go about doing it? And one other thing, If i create another partition, and install ubuntu on it, and later, i decide to get rid of ubuntu, could i recapture that partition with Mac OS X? So i can get that space back for OS X?

---

### Post by [-Ghost-] on 2007-06-05
I made an attempt awhile back to get a triple boot working with osx, ubuntu and windows xp, the boot never really worked right and i could only get into osx afterwards. I wanted to try another attempt, this time using vista in place of xp. How can i wipe my boot record to start from scratch? I don't mind losing my OSX install if that's necessary. Whenever i try to boot onto a Vista DVD to start an install i get taken to a grub bootloader and i can't use the keypad to move down from Ubuntu to Windows, or to even get an option to boot onto the DVD. Any suggestions?

---

### Post by PaaC on 2007-06-06
I am so bumping this. I also had a working Mac OS/Win XP setup made with boot camp and wanted to add another partition for Ubuntu. I booted from the GParted LiveCD and re-partitioned my hard-drive (please note that you have to disable journaling on the partition you want to re-size in order for GParted to read the HFS+ partition). I wiped the XP partition and shrinked my Mac OS partition and made two new ones, one FAT32 partition at the end of the disk and one ext3 in the middle.
When I booted into Mac OS it didn't want to mount the new partitions, but I tried booting into the WinXP CD anyway, but the partition manager just saw a big 120Gb disk, and not three partitions.
Okay, so I go into rEFIt and synchronize my partition tables and now WinXP's partition manager sees my partitions, but I can't install onto the FAT32-one for some reason. I now wipe the two FAT32 and ext3 partitions and creates a new FAT32 partition and am leaving some space for the ext3 one which I can format later.
Everything seems to be all-right until the first reboot and I see the WinXP logo, and then it blue screens.
I will try and reset my HDD into one partition, re-install rEFIt and read the documentation above and try again and will let you know how it goes.

---

### Post by ronocdh on 2007-06-07
> **'[-Ghost-] said:**
> I made an attempt awhile back to get a triple boot working with osx, ubuntu and windows xp, the boot never really worked right and i could only get into osx afterwards. I wanted to try another attempt, this time using vista in place of xp. How can i wipe my boot record to start from scratch? I don't mind losing my OSX install if that's necessary. Whenever i try to boot onto a Vista DVD to start an install i get taken to a grub bootloader and i can't use the keypad to move down from Ubuntu to Windows, or to even get an option to boot onto the DVD. Any suggestions?
I use rEFIt as my bootloader and then GRUB. I'm using WinXP instead of Vista, but I don't think that makes a difference. The problem of the unresponsive keyboard on the GRUB screen is universal, and it's due to a firmware issue, I believe. To get around it, you'll have to do a little wistful key-tapping voodoo. I personally hold the down arrow on the keyboard as soon as I choose my OS on rEFIt, and usually this means that when the GRUB screen loads, the selection highlight will be cycling downwards. Even still, you might have to do a hard shutdown every now and then to get it working.

You should know that by editing your GRUB file in Ubuntu, you can change the default selection on the screen, as well as reduce (or increase) the countdown timer.

---

### Post by ronocdh on 2007-06-07
> **PaaC said:**
> I am so bumping this. I also had a working Mac OS/Win XP setup made with boot camp and wanted to add another partition for Ubuntu. I booted from the GParted LiveCD and re-partitioned my hard-drive (please note that you have to disable journaling on the partition you want to re-size in order for GParted to read the HFS+ partition). I wiped the XP partition and shrinked my Mac OS partition and made two new ones, one FAT32 partition at the end of the disk and one ext3 in the middle.
When I booted into Mac OS it didn't want to mount the new partitions, but I tried booting into the WinXP CD anyway, but the partition manager just saw a big 120Gb disk, and not three partitions.
Okay, so I go into rEFIt and synchronize my partition tables and now WinXP's partition manager sees my partitions, but I can't install onto the FAT32-one for some reason. I now wipe the two FAT32 and ext3 partitions and creates a new FAT32 partition and am leaving some space for the ext3 one which I can format later.
Everything seems to be all-right until the first reboot and I see the WinXP logo, and then it blue screens.
I will try and reset my HDD into one partition, re-install rEFIt and read the documentation above and try again and will let you know how it goes.
Instead of using GParted, I recommend you wipe your drive and install OS X, as you've indicated. Then use the **sudo diskutil resizeVolume** command present in so many of the guides linked above to partition your drive three ways. Then install Windows XP (the procedure might be different with Vista, but you've only mentioned XP, and that's what I know myself), but make sure you have a drivers CD handy! (Burn this in Boot Camp, but don't partition with Boot Camp.) After WinXP is installed and updated with drivers, then boot from the Ubuntu CD and install that. Hopefully this helps, and post back if you run into any more trouble!

---

### Post by PaaC on 2007-06-17
Thank you for your ever so useful replies! I was trying the use the sudo diskutil resizeVolume command, but failed. Now I now that I had to repair my disk, but I just dusted of my Leopard copy and resized my volume purely by the GUI from the disk utility (see my post **[COLOR="DarkRed"][here]("http://ubuntuforums.org/showthread.php?t=469999")[/COLOR]**). Talking about Vista, I actually upgraded my XP install to Vista, but it is now driving me bonkers.. The UAC and all the other 'security features' are just awful..  ](*,)

---

### Post by Chrisj303 on 2007-06-18
> **ronocdh said:**
> I. The problem of the unresponsive keyboard on the GRUB screen is universal, and it's due to a firmware issue, I believe. To get around it, you'll have to do a little wistful key-tapping voodoo. I personally hold the down arrow on the keyboard as soon as I choose my OS on rEFIt, and usually this means that when the GRUB screen loads, the selection highlight will be cycling downwards. Even still, you might have to do a hard shutdown every now and then to get it working.
.

..or use LILO:p

---

### Post by davidek on 2007-06-18
that's means I didn't have that kind of problem with LILO (keyboard doesn't work on my macbook)? If ye how I can switch without lose all my OS?

thaks in advance :popcorn:

---

