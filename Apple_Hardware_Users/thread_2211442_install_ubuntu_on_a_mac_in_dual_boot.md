---
title: "install ubuntu on a mac in dual boot"
date: 2014-03-16
forum: Apple Hardware Users
---

### Post by flamant on 2014-03-16
Hello
I try to install ubuntu on my MAC book pro. I have a Mac book 9,2 (mid 2012) and try to install ubuntu 12.04.4

I installed reflt and created a 50 GO partition formated in hsf+

I passed successfully the stage of burning the MAC version "ubuntu-12.04.4-desktop-amd64+mac.iso" to a DVD and getting the installation menu.

My questions are the following:
When I launch the installation from the DVD, it takes too much time and I had to stop the proccess being afraid that the installation will format my entire hard drive for ubuntu.
Do you know if it is normal that it takes so much time and is there a menu that appears after a certain time to choose the adequat partition and format it for ubuntu (for example in ext4 format) ?
Do I run the risk of overwrite OS X and all the data on my main partition ?
If somebody has experienced installing ubuntu 12.04 (or other release) on MAC how many time does it take ?

Thank you in advance for your answers.

---

### Post by bapoumba on 2014-03-16
Moved to Apple Users.

---

### Post by PartisanEntity on 2014-03-18
Yes, the installation process will offer you the chance to choose with partition to use, and also to format it. Do not worry, the installation process will not install to a partition or format anything without your permission.

Maybe try to give it a little more time? How long approximately have you waited?

---

### Post by oldfred on 2014-03-18
I do not know Mac, but some links.
Linux will not install to a Mac formatted HFS+ partition. 
refit is old, and you may be better off with rEFInd.

 [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

      
 [https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by flamant on 2014-03-27
Hello, 

I installed ubuntu from a DVD (iso image) ignoring the following message

> 
The partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked for use as a "reserved BIOS boot area" and should be at least 1MB.
If you do not go back to the partitioning menu and correct this error, boot loader installation may fail later, although it may still be possible to install the boot loader to a partition



And I restart and get the menu reflt that allow me to connect on ubuntu with the partition ext4






   one thing bothers me:


When I inspect my partitions, I can't see the swap partition to bootload on ubuntu but nevertheless it works. I would like to do the things properly and I tried to follow a French tutorial so to get a swap partition

Once I am connected on ubuntu, I open a terminal window and I enter the following commands

```

sudo su -
mkdir /mnt/ubuntu
mount /dev/sda3 /mnt/ubuntu (remplacez sda3 par la partition choisie) mount -t proc none /mnt/ubuntu/dev
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash
dd if=/dev/zero of=/swapfile bs=1024 count=1024000 (cette commande prend envirion 30 secondes a&#768; s'exe&#769;cuter)
mkswap /swapfile
swapon /swapfile
echo "/swapfile swap swap defaults 0 0" >> /etc/fstab

apt-get install grub
grub-install /dev/sda3 (remplacez sda3 par la partition choisie) update-grub
reboot

```

But I can't see a swap partition afterwards

Do you have a clue ? Thank you in advance for your answers

---

### Post by andy10 on 2014-03-28
I don't have an answer to your question but i'll provide this information on my Macpro dual boot for what it is worth:

  	 	 	 	   I have a MacBook Pro 9,1 (Mid 2012). I have installed Xubuntu 14.04 on it (I have tried Ubuntu 14.04 as well). I used the OS X Boot to recovery system to resize the OS X Lion partition to half of the 500gb disk space and left the other half blank. I then installed rEFInd on the OS X partition.  

 

 I put the Xubuntu 14.04 image on a usb stick and booted it using rEFInd.  I selected &#8220;something Else&#8221; as the install choice and set up the free space with 10gb for the &#8220;/&#8221; partition 16gb for the swap space as I have 16gb RAM, probably overkill, and the remainder as &#8220;Home.&#8221;  
 

 I also selected the Xubuntu partition as the location for the GRUB installation location. REFInd provides the boot choices for you now and you can choose Linux or OS X at boot time. Everything is working fine on my machine. I do use a script called &#8220;control&#8221; in a cron job as described on this web page ( [http://unencumberedbyfacts.com/2013/08/16/linux-on-a-macbook-pro-101/](http://unencumberedbyfacts.com/2013/08/16/linux-on-a-macbook-pro-101/) ) to control the fans and have better control of the heat.
 

 Hopefully, this will be of some help to you.
 

 Andy

---

### Post by flamant on 2014-04-01
Thank you andy10 for your answer

---

