---
title: "Vista Ubuntu mess"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by misterz on 2007-12-13
Previously, I had Ubuntu and XP Pro on a dual boot (Grub) with no trouble. Then, I go to upgrade to Vista Ultimate. No more Ubuntu. Then, I go to reinstall Ubuntu. No more Vista. Then, I do the followiing, as per some online advice ([http://apcmag.com/5045/how_to_dual_boot_vista_with_linux):](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux):)

When the CD loads, launch a terminal window (Applications > Accessories > Terminal).
In the terminal, type: 
sudo grub 
This will put you in superuser mode and launch the GRUB application.
To find the partition with the GRUB boot files, type in: 
find /boot/grub/stage1
Ubuntu & Vista - sudo grub
The response should be “(hd0,0)” or something similar – this is where you need to reinstall GRUB. 
Set this location as root for the current session:
root (hd0,0) 
Ubuntu & Vista - set root
Then type in:
setup (hd0,0)
This will reinstall the GRUB bootloader to disk 0, partition 0. If you type in “setup (hd0)” then GRUB will be reinstalled to the MBR and will overwrite Vista’s bootloader. 
Ubuntu & Vista - setup grub
Type in “quit”, exit the terminal window, and you’re done. Reboot the system and boot into Vista (at this point, you still won't see any option to boot into Linux). 


Now, when I install the Vista CD (yes, the bios is set to boot from the CD), it goes right back into Ubuntu. So..., what now? I'm looking to dual boot Ubuntu and Vista Ultimate. Can someone get me there from here?

---

### Post by Dr Small on 2007-12-13
I would wipe everything and start completely over. (That's just me...)
Install vista first, and then Ubuntu.

---

### Post by misterz on 2007-12-13
I can't. Ubuntu won'
t recognize the Vista disk. I don't know where to begin.

---

### Post by rsambuca on 2007-12-13
So if you just boot the computer with no CD's in the drive, it goes straight into Ubuntu?  or does it go to a grub menu first.  Either way, if you get into Ubuntu, please enter this command in a terminal and post the output here.

sudo fdisk -l

---

### Post by misterz on 2007-12-13
OK, but what will that do?

---

### Post by rsambuca on 2007-12-13
It will tell us the structure of your hard drive.

---

### Post by misterz on 2007-12-13
I get no response. Just returns to >

---

### Post by rsambuca on 2007-12-13
Are you running Ubuntu currently?

---

### Post by misterz on 2007-12-13
Yes

---

### Post by bartos on 2007-12-13
When you install Ubuntu, at final install page where it shows you all the options you selected. There is an advanced button at bottum. It has option of where to load grub. Tell it install grub to Ubuntu partion ( eg hd0,1 for first disk ,partion 2) and not the MBR of your hard drive
let ubuntu install. Pull out Ubuntu disk at end of install for reboot and insert Vista disk.Reboot and bring up Vista recovery options and repair bootloader.

With Vista now booting. Download EasyBCD and setup Vista bootloader with this program to give an option to boot Linux (Ubuntu )

Good luck as it worked for me.:)

---

### Post by Dark_Stang on 2007-12-13
You're using sudo, right? If you do it as a normal user it does nothing. If you run as a super user it gives you the partitions.

---

### Post by rsambuca on 2007-12-13
Open a terminal and then copy and paste the following into the terminal, and then press enter:```
sudo fdisk -l
```Please do not type it.  Please copy and paste it.

---

### Post by misterz on 2007-12-13
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000617f4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4702    37768783+  83  Linux
/dev/hda2            4703        4865     1309297+   5  Extended
/dev/hda5            4703        4865     1309266   82  Linux swap / Solaris
mark@mark-desktop:~$

---

### Post by rsambuca on 2007-12-13
OK, you obviously wiped Vista since there is no ntfs partition.  If you want to install Vista again, you will have to get into your bios and set the CD as the first boot device.

40GB is getting pretty tight to be dual booting Vista with anything, by the way!

---

### Post by misterz on 2007-12-13
Well the 40GB was adequate. I gave 20 GB and I'm just using this unit to explore both Ubuntu and Vista. But anyway, I believe the unit's set to boot off the CD. At any rate, what's to prevent the same problem again. That is, I get Vista up and running. Then, I go to install Ubuntu. Then, I'm back where I was before with Ubuntu instead of Vista.

---

### Post by rsambuca on 2007-12-13
If you are willing to start fresh, the easiest way is to use the Ubuntu liveCd or gParted liveCd to split the drive into two, one for Vista (ntfs), and one for Ubuntu (ext3).  Then Install Vista onto the first partition, and then install Ubuntu into the pre-setup second partition.  Grub will detect Vista and will give you a choice at bootup whether to run Vista or Ubuntu.

---

### Post by misterz on 2007-12-13
Could use a step by step

---

### Post by Yellowdog428 on 2007-12-14
Google is you friend  :wink:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

Here is a screen cast, it is an install of Dapper but mostly still current

[http://video.google.co.uk/videoplay?docid=-2369893842637434537](http://video.google.co.uk/videoplay?docid=-2369893842637434537)

Cheers

---

