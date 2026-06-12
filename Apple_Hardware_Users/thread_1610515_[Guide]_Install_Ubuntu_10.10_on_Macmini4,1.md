---
title: "[Guide] Install Ubuntu 10.10 on Macmini4,1"
date: 2010-10-31
forum: Apple Hardware Users
---

### Post by kernel_script on 2010-10-31
For reference, take a look on the Ubuntu Wiki, about [Ubuntu 10.10 on Macmini4,1]("https://help.ubuntu.com/community/Macmini4-1/Maverick") first, before reading/following this guide.

Download and burn the **alternate CD** version of **Ubuntu 64 Bits**:

**[SIZE="3"]DIRECT DOWNLOAD[/SIZE]**
[http://releases.ubuntu.com/maverick/ubuntu-10.10-alternate-amd64.iso](http://releases.ubuntu.com/maverick/ubuntu-10.10-alternate-amd64.iso)

**[SIZE="3"]TORRENT DOWNLOAD[/SIZE]**
[http://releases.ubuntu.com/maverick/ubuntu-10.10-alternate-amd64.iso.torrent](http://releases.ubuntu.com/maverick/ubuntu-10.10-alternate-amd64.iso.torrent) (Torrent didn't work for me)


**[SIZE="3"]TRI BOOT INSTALL[/SIZE]**

I'll be doing a Tri Boot Install, but you can easily, with that knowledge, do a Dual or Single Boot Install.

**1. Partitioning - Preparing for installation**
 - Boot into OS X;
 - Open Bootcamp utility;
 - Create a partition for Windows (will be sda3) and make it 1/3 of the disk size. Create this partition as FAT;
 - Now create a partition for Ubuntu (will be sda4), also 1/3 of the disk size of course. Don't forget to create it a little bit larger because of the extra for SWAP (will be sda5).


**2. Installing Windows** 

*In a Tri Boot Install scheme, you need to install Windows first, otherwise it will mess up MBR and give you lots of headaches.*

 - Boot into OS X;
 - Insert your Windows DVD Install disk;
 - Restart your Mini and quickly press and hold the **C** key until Windows starts the installation process.


**3. Installing Ubuntu**
 - Boot into OS X;
 - Insert your Ubuntu CD Install disk;
 - Restart your Mini and quickly press and hold the **C** key until Ubuntu starts the installation process;
 - Press **F6**. Choose **noacpi** and **nomodeset**. Press **ESC** and **Return**;
 - On the installation wizard, choose manual partitioning;
 - Probably, your partitions looks like the following:

sda2 - Mac OS X - hfs
sda3 - Windows - fat
sda4 - Ubuntu - fat

 - Choose to edit **sda4**, resize it as to leave a *extra for SWAP*. Choose **ext4** as the file system. **/** as the main directory for installation and mark the partition as **bootable**. Save and go back to the partition table;
 - Now choose the empty extra space destined for **SWAP**. Edit it and choose *SWAP as file system*.
 - Finish the table partitioning and begin installation.
 - While in the installation process, you'll be asked for where to install GRUB. **Choose sda4**, or, the same partition you're using to install Ubuntu.


**[SIZE="3"]POST-INSTALLATION[/SIZE]**

You can install some multi-os bootloader to ease your life. Make a quick search on your favorite Internet search engine about "tri boot mac linux" and you'll see some nice options.

To boot properly into Ubuntu, in the grub menu, press the **E** key and
edit and add the following:

> linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=53658b6a-2991-4a15-8e48-8ab7d4e0985c ro   quiet **nosplash noacpi nomodeset reboot=acpi**

Press **Ctrl+X** to exit and boot.

Install NVIDIA Drivers from the repository to get resolution straight. Do the same for the Wireless Card. (*System > Administration > Hardware Drivers*)

For proper boot, restart and shutdown, log in into Ubuntu. Press **Alt+F2** and Copy and Paste+Return the following (You'll need to do this every time you update your kernel):


> gksu gedit /boot/grub/grub.cfg


Find the part that says something like the following (just around line 64. You can set it to 0 for automatic boot):


> set timeout=10


Now find the following (around line 78 ) :


> linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=53658b6a-2991-4a15-8e48-8ab7d4e0985c ro   quiet splash


Edit and Add the following:


> linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=53658b6a-2991-4a15-8e48-8ab7d4e0985c ro   quiet **nosplash noacpi nomodeset reboot=acpi**


Save and exit.


Fixing Audio and Bluetooth: [**here**]("https://help.ubuntu.com/community/Macmini4-1/Maverick")

-------------

If you liked my guide, please visit [my Blog]("http://openmindlifestyle.wordpress.com/") to see my other works, like Howtos, Art, Tips etc. No I don't have paid advertisement, so don't worry.

This guide was not possible without the love and caring support of the awesome Ubuntu community. Special thanks goes to:

**Stevethepirate** and **HashBox** on Ubuntu IRC Channel for helping me out with GRUB.

**Yako no Kai** - [http://ubuntuforums.org/showthread.php?t=1323102&page=2](http://ubuntuforums.org/showthread.php?t=1323102&page=2) - for finding out how to restart Ubuntu properly.


Be well. See ya.


**[SIZE="3"]REFERENCES[/SIZE]**
Ubuntu Forums
Ubuntu IRC Channel
[Ubuntu Wiki]("https://help.ubuntu.com/community/Macmini4-1/Maverick")

---

### Post by kernel_script on 2010-11-18
**Update**

 *- New and improved guide.*

---

