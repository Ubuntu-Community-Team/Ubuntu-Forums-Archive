---
title: "Installing Backtrack 5 on external hard drive"
date: 2012-10-14
forum: Any Other OS
---

### Post by Bronk12 on 2012-10-14
Hello guys,

I have been trying to find some good information on how to install backtrack to my external drive but there isnt much about it. I have asked at the backtrack forums but nothing from them yet.
I decided to ask here since backtrack is based on ubuntu.

Basically I want to install backtrack on my external drive. I have a new one with 1 TB and want to use all of it for backtrack. I need help with the partitioning and correct procedure for the installation.
I dont want to mess up my windows installation in any way so I decided to ask for some help.
Anything you can do to help me out here would be appreciated.

---

### Post by daslinkard on 2012-10-14
Welcome to the Forums!  This really should be under Other OS/Distro Talk but after doing a quick Google search I found this [link]("http://www.linuxbsdos.com/2012/03/12/install-backtrack-5-revolution-2-on-external-hard-drive/") which you may find to be informative.

---

### Post by wildmanne39 on 2012-10-14
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by danelwillis on 2012-10-14
Plug in your external harddrive, follow all the basic intrutions till you get to the point where your giving 3 maybe more options about how much memory to allocate to the new partition. Then click manually wipe all partitions then change using the dropdown combo box and select your hard drive. It is usually DEVSDB it will then say the size. Make sure you select the external hard drive here. Continue with the normal instructions through out the rest of the install. When this is all complete install gparted, or equivalent to resize the partition manually, this will actually cause Backtrack to work more stably. Hope this helps.

---

### Post by Bronk12 on 2012-10-14
> **daslinkard said:**
> Welcome to the Forums!  This really should be under Other OS/Distro Talk but after doing a quick Google search I found this [link]("http://www.linuxbsdos.com/2012/03/12/install-backtrack-5-revolution-2-on-external-hard-drive/") which you may find to be informative.
Thank you!
Yeah I have read that one as well but according to the folks at the backtrack forums it wont work and also on the last screenshot the installation guide is showing that sda which is the internal drive will also be formatted but the guy is talking about installing on external hard drive.
I dont want any changes to be done on my internal hard drive.

---

### Post by Bronk12 on 2012-10-14
> **danelwillis said:**
> Plug in your external harddrive, follow all the basic intrutions till you get to the point where your giving 3 maybe more options about how much memory to allocate to the new partition. Then click manually wipe all partitions then change using the dropdown combo box and select your hard drive. It is usually DEVSDB it will then say the size. Make sure you select the external hard drive here. Continue with the normal instructions through out the rest of the install. When this is all complete install gparted, or equivalent to resize the partition manually, this will actually cause Backtrack to work more stably. Hope this helps.
Thanks for your reply here mate.
So what you are saying is that I should wipe the entire drive instead of formatting the partitions manually. And after that partiton it with gparted. But doesnt backtrack need 3 partitions for the install and to be able to boot from it?
root, swap and the boot partition?
I am getting confused here...

---

### Post by oldfred on 2012-10-15
These are standard Ubuntu installs, so screens look a bit different. But install process is the same.

You need / & swap but we normally suggest /home as a separate partition. With any second drive or external or flash drive you want to be sure to install the grub2 boot loader to the MBR of the external device. All the default installs will put grub's boot loader in sda which usually is the internal drive. That can be fixed but better not to have to.

You only get the choice on where to install the boot loader with manual install with Ubuntu, not sure about Backtrack. With Ubuntu it is the combo box at the bottom of the partitioning screen. It also will default to the drive that is sda, so you must change to the drive that is the external.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Bronk12 on 2012-10-15
> **oldfred said:**
> These are standard Ubuntu installs, so screens look a bit different. But install process is the same.

You need / & swap but we normally suggest /home as a separate partition. With any second drive or external or flash drive you want to be sure to install the grub2 boot loader to the MBR of the external device. All the default installs will put grub's boot loader in sda which usually is the internal drive. That can be fixed but better not to have to.

You only get the choice on where to install the boot loader with manual install with Ubuntu, not sure about Backtrack. With Ubuntu it is the combo box at the bottom of the partitioning screen. It also will default to the drive that is sda, so you must change to the drive that is the external.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)
thanks for the help.
I will read the guides you posted and see if that is what I need.
Cheers

---

