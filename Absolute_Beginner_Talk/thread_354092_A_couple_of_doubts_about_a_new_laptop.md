---
title: "A couple of doubts about a new laptop"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-02-05
I have a couple of doubts about buying a laptop.
[LIST]
[*]the first one: Does Xubuntu recognizes the fingerprint reader? 
[*]the second one: Does dual-boot can be done in partitions? I mean one partition for windows and another for xubuntu?
[*]the third one: If I do dual-booting I'd like to have a  third partition with music, and video... and those files, so in order to share those files between windows and linux does it needs to be a fat32 partition? or is there a better type that works on both, and in cas there isn't one, how do you repair the "wasted" space on that partition?
And making this  part of the doubt 3, how do I move the Home directory into a third partition?
[/LIST]

---

### Post by Shatrat on 2007-02-05
1. No idea, I've never dealt with fingerprint readers.
2. Yes, this is the standard way to do it.
3. You can read and write Ext3 filesystem from windows using the driver from fs-driver.org, and you can read NTFS easily from linux and write as well, but writing isnt 100% safe because NTFS is not documented.  There really isnt a reason to use Fat32 anymore, and its not a very good filesystem format anyway.  
You can easily make a seperate partition for your /home and mount it there during the installation process.  This can be very useful when reinsalling or upgrading because all your personal settings are stored in /home.

PS, xubuntu is often recommended for older laptops with weak hardware, but you could just as well run normal ubuntu or kubuntu on any modern laptop.  I'm not sure why you mentioned xubuntu, but if youre worried about system resources you're probably fine with anything manufactured in the last few years.

---

### Post by shoot2kill on 2007-02-05
1 - Fingerprint Scanner - Unknown.. Sorry
2 - For what your using, try:

--Hard Disk 1--  Ubuntu Partition - ~30% - Ext3
--Hard Disk 1--  Windowze Partition - ~30% - NTFS
--Hard Disk 1--  Music & Vids Partition - ~30% - FAT32 - (i would use FAT32 as the NTFS file system is UNSTABLE for writing to)

Obviously Partition Sizes (%ages) can be changed... 

Also, after a coupl of dual boot attempts myself, Install Windowze first on as much HDD space you need, and also create the FAT32 partition whilst in Windowze. then install Ubuntu on the remaining sace..

---

### Post by 23meg on 2007-02-05
> the first one: Does Xubuntu recognizes the fingerprint reader?Some but not all fingerprint readers are supported by the kernel; I think those in Thinkpads at least. You can find out by doing a web search.

---

### Post by Jorge32 on 2007-02-07
the fingerprint reader is the one included in the laptop.. it is a HP Compaq nx6325
I fear it doesn't works on xubuntu, and I also have fears asif I'll lose the buttons with functions as the change screen and things like that.
where can i find info about it?

---

### Post by sherbyx on 2007-02-21
Until now no one has managed to set the nx6325 fingerprint reader in any linux distro. They are working on it. You can find some info here [http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nx6325](http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nx6325)
But I don't think that it will be ready too soon. The rest of the hardware works but I recomand you to use kubuntu 6.10 or at least ubuntu 6.10 on 32bit (xubuntu may have some problems with the soft keys). The 64bit version has a lot of incompatibilities ([https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325](https://wiki.ubuntu.com/LaptopTestingTeam/HPNX6325)) so don't use it if you don't use some 64 bit applications (mathlab, simulations, or other scientific optimized stuff)

A good howto regarding ubuntu on nx6325 can be found here [http://vale.homelinux.net/wordpress/?p=106](http://vale.homelinux.net/wordpress/?p=106)

---

