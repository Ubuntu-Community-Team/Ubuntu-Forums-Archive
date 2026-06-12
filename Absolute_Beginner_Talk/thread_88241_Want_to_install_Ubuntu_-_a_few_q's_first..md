---
title: "Want to install Ubuntu - a few q's first."
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by thedanielm on 2005-11-09
Alright, i plan to swith to ubuntu from winxp within the next few days but first i have a few questions/concerns.  

Right now i am connected to the internet through a wireless router and a US Robotics USB wireless adapter.  Am i going to have unlimited problems getting the USB wireless to connect/function with encryption etc?

Also, I currently have 2 drives on the xp system. a baby drive(20gb) for the windows installation and program files while i have another(120) for music movies downloads and whatnot.  I would be installing ubuntu on one drive and using the other drive for storage.  I would like to be able to keep what i have on the storage drive.  Is this possible? i realize that the storage drive uses NTFS in windows.  Or do i have to somehow back everything up on dvd's and reformat.

Hope someone can enlighten me.

i shall post more q's here as they pop into my head. 
btw, i have installed ubuntu on my old comp and basically i got hooked,  I mostly just browse the web, chat on msn, use spreadsheets, word..., bit torrent and maybe a bit of Enemy Territory so i figure i can do all that on ubuntu and be happy.

Thanks!

---

### Post by aysiu on 2005-11-09
[QUOTE=thedanielm]
Right now i am connected to the internet through a wireless router and a US Robotics USB wireless adapter.  Am i going to have unlimited problems getting the USB wireless to connect/function with encryption etc?[/quote] Best way to know is to try out the live CD and tinker around.

> 
Also, I currently have 2 drives on the xp system. a baby drive(20gb) for the windows installation and program files while i have another(120) for music movies downloads and whatnot.  I would be installing ubuntu on one drive and using the other drive for storage.  I would like to be able to keep what i have on the storage drive.  Is this possible? i realize that the storage drive uses NTFS in windows.  Or do i have to somehow back everything up on dvd's and reformat. NTFS is read-only. Some people vouch by a program called Captive NTFS that supposedly enables NTFS write ability, but you're better off making the storage drive FAT32. A great guide for partitioning a dual boot is [this one](http://users.bigpond.net.au/hermanzone/).

---

### Post by blastus on 2005-11-09
[quote=thedanielm]Also, I currently have 2 drives on the xp system. a baby drive(20gb) for the windows installation and program files while i have another(120) for music movies downloads and whatnot. I would be installing ubuntu on one drive and using the other drive for storage. I would like to be able to keep what i have on the storage drive. Is this possible? i realize that the storage drive uses NTFS in windows. Or do i have to somehow back everything up on dvd's and reformat.[/quote]

I would backup everything important even if you were going to reinstall Windows. It really depends on what you want to do. If you want to just use Windows for games and use Ubuntu for everything else, then the cleanest way would be to backup everything and reorganize your system like this:

**120Gb DRIVE (PRIMARY MASTER, /dev/hda):**

**/dev/hda1:** format NTFS and install Windows XP on it
(depending on your needs, 20Gb may be fine)

**/dev/hda2:** format ext3 and install Ubuntu on it
(120Gb - /dev/hda1 - /dev/hda3 sizes)

**/dev/hda3:** Linux Swap (designated Ubuntu swap partition)
(size according to the amount of RAM you have)

**20Gb DRIVE (PRIMARY SLAVE, /dev/hdb):**

**/dev/hdb1:** format ext3 
(18Gb - use for backup)

**/dev/hdb2:** format FAT32
(2Gb - use for temporarily sharing data between Windows and Ubuntu)

Of course, this means reinstalling everything--it's a lot of work but it's worth it. You are better off installing Windows and Ubuntu on your 120Gb drive because it will be faster than the 20Gb drive. You can use the partition manager in the Ubuntu installer to resize partitions if you prefer.

---

### Post by thedanielm on 2005-11-10
ok i guess i didnt mention a few things,  Im going to ditch the 20gb drive and thrown it in another computer that is going to be used as a network media player for my home entertainment system. 
my main system will consist of 160gb and 120gb drives. (the 160 being new and faster)
I do not want a dual boot system with winxp.  I guess my only option is to backup my stuff and start from scratch... 10 dvd's later...

good call on trying stuff out with live cd, never thought of that.

---

### Post by aysiu on 2005-11-10
You don't have to start from scratch. Here, read [this](http://users.bigpond.net.au/hermanzone/).

---

### Post by thedanielm on 2005-11-10
Alright, fired in the live cd, it recognizes my US robotics usb adapter in the device manager. now how in the heck do i get it to connect and enter the encryption keys.

also in regards to the last link on partitoning and whatnot, is it saying that i can creat a fat32 partition out of the freespace on my music drive. then move all the files there and extend the partition to erase all the data in ntfs?

Sorry im a noob here.

---

