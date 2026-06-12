---
title: "ununtu Live CD on XP"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by zinc00 on 2007-09-26
I have XP pro and I reboot to ubuntu 7.4 using live cd...
Question is:
During my ubuntu usage, how or can i save any changes...since I only booted from ubuntu?
Or maybe I should make a small partition for it on my HD (250GB) If so how? How much space does it need?
thx :)

---

### Post by ukripper on 2007-09-26
you can dual boot ubuntu -  XP, create ubuntu partition atleast 20 GB to be fair and rest depends upon you.. and your needs..

Booting from Live Cd wont save any changes until you install ubuntu on partition

follow this guide for installtion [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by misfitpierce on 2007-09-26
As said Live CD wont save changes. I'd agree if you need windows that bad to make a partition for Ubuntu.

---

### Post by zinc00 on 2007-09-26
**thx ppl :)**

---

### Post by Dr Small on 2007-09-26
> **misfitpierce said:**
> As said Live CD wont save changes. I'd agree if you need windows that bad to make a partition for Ubuntu.
I personally do not agree with that, as setting up another partition and installing Ubuntu on it, if you want to keep Windows is the way to go, as you can then daul-boot, and have both operating systems at once.

Dr Small

---

### Post by dn_desaku on 2007-09-26
I would not use the Ubuntu as a LiveCD for everyday use because it is pretty bare by default. If you don't want to install it (or too afraid too) use a distro where the focus is the Live CD. I personally use Slax Kill Bill Edition because it comes with WINE and DosBox. :lolflag:

Also, in your case it is useful because all the settings can be saved in a conifg file. It can be loaded every time you start SLAX. 
Now, as for partitioning. Make a FAT32 partition so Linux and Windows can read it and save files on it. 
This is really useful for backing up data for both OSes. But note you can't install Ubuntu on FAT32. 

Even if you're going to install it in the end, make a small (1~5 GB, depending on needs) FAT32 partition so it can be read/written by Windows and Linux. :guitar:
But make Ubuntu its own partition in the end. Mine is set to 14GB

---

### Post by Niniel on 2007-09-26
Haha, that's a great name, I have to check it out. 

Lol, they like to pretend this is named after the movie. :)

---

### Post by dn_desaku on 2007-09-26
Ubuntu's great and all but having one or more OSes on hand is handy.

Check out SLAX: 
[http://www.slax.org/download.php](http://www.slax.org/download.php)

---

### Post by rsambuca on 2007-09-26
> **dn_desaku said:**
> Now, as for partitioning. Make a FAT32 partition so Linux and Windows can read it and save files on it. 
This is really useful for backing up data for both OSes. But note you can't install Ubuntu on FAT32. 

Even if you're going to install it in the end, make a small (1~5 GB, depending on needs) FAT32 partition so it can be read/written by Windows and Linux. :guitar:
But make Ubuntu its own partition in the end. Mine is set to 14GB

FAT32 is not the best filesystem by any means. I prefer just to use the Windows FS-drivers to read/write to ext2/3 and the ntfs-3g linux drivers to read/write to your Windows drives.  Saves you from an unnecessary partition.

---

### Post by dn_desaku on 2007-09-26
> **rsambuca said:**
> FAT32 is not the best filesystem by any means. I prefer just to use the Windows FS-drivers to read/write to ext2/3 and the ntfs-3g linux drivers to read/write to your Windows drives.  Saves you from an unnecessary partition.

Yeah, that is better. But since I use Vista (as we all know Vista is not so good with the install of software as it is still rather new) I'm a little afraid of installing drivers to read/write Linux partitions. 

So I'm going to wait. If anybody can tell me where to get a driver to read Linux partitions for Vista, drop me a line. I would install XP, but I can't get my hands on an XP Pro CD and I'm not using pirated copies. Sucks that Vista came out so soon and M$ is going to snipe XP soon.

---

### Post by rsambuca on 2007-09-26
> **dn_desaku said:**
> Yeah, that is better. But since I use Vista (as we all know Vista is not so good with the install of software as it is still rather new) I'm a little afraid of installing drivers to read/write Linux partitions. 

So I'm going to wait. If anybody can tell me where to get a driver to read Linux partitions for Vista, drop me a line. I would install XP, but I can't get my hands on an XP Pro CD and I'm not using pirated copies. Sucks that Vista came out so soon and M$ is going to snipe XP soon.

The fs-driver works in Vista as long as you use the "compatibility mode" for XP when installing it.

---

### Post by bodhi.zazen on 2007-09-26
> **dn_desaku said:**
> Yeah, that is better. But since I use Vista (as we all know Vista is not so good with the install of software as it is still rather new) I'm a little afraid of installing drivers to read/write Linux partitions. 

So I'm going to wait. If anybody can tell me where to get a driver to read Linux partitions for Vista, drop me a line. I would install XP, but I can't get my hands on an XP Pro CD and I'm not using pirated copies. Sucks that Vista came out so soon and M$ is going to snipe XP soon.

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

Other very nice live distros include Wolvix and Zenwalk (live edition)

---

### Post by dn_desaku on 2007-09-26
Thanks, rsambuca and bodhi.zazen I installed the driver and it works. Though, I still prefer having a seperate FAT32 partition but that's just me :lolflag:

---

