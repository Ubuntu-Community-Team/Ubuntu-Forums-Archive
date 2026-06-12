---
title: "Unable to create partition when installing on USB stick"
date: 2017-10-29
forum: Apple Hardware Users
---

### Post by nathanlcht on 2017-10-29
Hello.

[COLOR=#111111][FONT=Ubuntu][FONT=inherit]I have one of the latest Macbook (2017, Touchbar) and I am trying to install Ubuntu on it. VirtualBox being too slow, I decided to dual boot it but I don't have a lot of storage so I finally bought a 64GB Usb Stick to install Ubuntu on it.[/FONT]
[FONT=inherit]First step, I followed tutorials to download the .iso, convert it with hdiutil, format my usb key to be bootable and put the image file on the usb key. Then I restart my mac and by pressing the option key and booting on the usb, I get to a menu where I can choose between Install ubuntu and Try ubuntu.[/FONT]
[FONT=inherit]I have tried both but it doesn't work. In both cases, I first have to choose a language, then if I want to connect to wifi and then if I want to install updates automatically and install third-party softwares. I answered no to the last three items and moved to the next step. [/FONT]
[FONT=inherit]I then have to "choose an installation type" ie partition my usb key. In most of the tutorials I found, people could choose to partition automatically or even to install ubuntu automatically without this step, but I didn't have such options. [/FONT]
[FONT=inherit]So I clicked "create a new partition table" then created a boot partition of 250MB (EFI), a root / of 15GB (ext4), a swap of 4GB and a /home with the remaining space (ext4). I have tried several others partitioning with stuff I found online but each time, when I click Install, it tells me it failed to create a partition or a file system and I can't continue the installation (next step would be to choose my city for the time GMT).[/FONT]
[FONT=inherit]Any idea on what I did wrong or on how I could get the partitioning step done automatically? Thanks. [/FONT]


[/FONT][/COLOR]

---

### Post by oldfred on 2017-10-29
Moved to the Apple sub-forum. So those who know Mac can help.

I normally partition in advance with gparted and then use Something Else to choose the partitions I created.
Do not confuse the ESP - efi system partition (FAT32) and an Ubuntu /boot partition. With UEFI you must have the ESP, but most desktops do not need a separate /boot partition.

Post this:
sudo parted -l
And this for your flash drive, example with sdc, but use your drive:
sudo gdisk -l /dev/sdc

If you used flash drive as installer, it may not have standard partitions as most create a hybrid DVD/flash drive that does not use partitions. But then normal partition table space has random data which usually prevents partitioning. Partition table space just needs to be zeroed out.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Postrequisites_-_restore_the_USB_stick](https://help.ubuntu.com/community/Installation/FromUSBStick#Postrequisites_-_restore_the_USB_stick)

Note issues on full install to any drive other than first drive with UEFI & grub.
UEFI only boots from /EFI/Boot/bootx64.efi on USB flash drives. (I assume Mac is same?)
Grub only installs to first drive usually sda, and /EFI/ubuntu in ESP on first drive.
We have to manually copy /EFI/ubuntu twice to flash drive. Once to /EFI/ubuntu and once to /EFI/Boot and then rename shimx64.efi to bootx64.efi. The Ubuntu copy of grub/shim is hard coded to look for more files in /EFI/ubuntu, so both copy of both folders required.
You also need to edit fstab with UUID of flash drive's ESP, as install will have sda's UUID.
Best to do this before shutting down from install as you can boot flash drive from UEFI entry, but ESP default permissions are none, or you cannot see /EFI/ubuntu from working install, normally.

---

### Post by nathanlcht on 2017-10-29
I am not an expert in this so I didn't entirely understand what you wrote, but I will try one more time tonight, I first need to create a backup without partitioning.

In the meantime, I just wanted to make sure of something: is it actually possible to install Ubuntu on the same flash drive than the one I'm booting it from? I also decided to install it on an usb stick because it wouldnt work on my mac. I never get the menu where I'm supposed to select "Something else" when installing Ubuntu and I have no idea why. I would prefer having ubuntu on my drive rather than on my usb key if it is possible, but as I never even get the option to partition it automatically, if I do the partition in advance, I'd probably not get the Something else (except if it's related?). 

Also, while partitioning what I mentioned in my first post, I only had the choice to do it on the usb key, I couldn't select any other drive. 

Thanks.

---

### Post by oldfred on 2017-10-29
Very difficult to install to same flash drive as you boot.
And best to keep live installer as a repair tool for future issues.

I saved some links, but do not have nor know about Macs. Someone who has a Mac should be able to help.

 [http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf](http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf)
[http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)
[http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios](http://askubuntu.com/questions/732611/while-installing-ubuntu-on-a-mac-should-i-install-it-under-efi-or-bios) 
   Install to Mac
[https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640](https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) 
   FAT32 format  & label with boot flag on Mac
[https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation](https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation)
Mac full install UEFI boot to flash drive
[http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528](http://askubuntu.com/questions/886528/why-did-ubuntu-16-04-2-install-the-loader-on-macbook-pro-hard-drive-despite-bein?noredirect=1#comment1384515_886528)
[https://help.ubuntu.com/community/MacBookPro12-1/Wily](https://help.ubuntu.com/community/MacBookPro12-1/Wily)

---

### Post by sudodus on 2017-10-29
It is a good idea to backup now :-)

It is possible to install Ubuntu on the same flash drive as you are booting it from, if you boot with the boot option **toram**.

But it is a complication, and if you fail you have to start from the beginning and make it a live & installer drive again. I would recommend to install from one USB drive to another [USB] drive.

---

### Post by nathanlcht on 2017-10-30
Hi! 

So I gave up on the idea of installing it on the USB key, I have enough storage left on my Mac.

I followed this tutorial ([http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf](http://courses.cms.caltech.edu/cs171/materials/pdfs/How_to_Dual-Boot_OSX_and_Ubuntu.pdf), thanks oldfred!) and thought I was saved, but no. I have no problems with step 1 and 2, ubuntu is bootable on my USB key and I have partitioned my HD (except that for the boot loader, I had to make it 2.5GB because I couldn't partition smaller, but whatever).

But then, it comes back to the same issue. I go for "Try ubuntu without installing" and then "Install ubuntu" on the desktop. I select the language but when it comes to the "Installation type", I still don't have this menu (replace Windows with Mac):

[IMG]https://i.stack.imgur.com/Oh3pu.png[/IMG]

Instead, I directly have something like this:

[IMG]https://i.stack.imgur.com/Pj1wt.png[/IMG]

(pics taken from the Internet, not mines). Which is the same screen that I had before following the tutorial, ie when I launched the installation without having partitioned my mac (so it doesn't find it? it is marked available though in disk utility app). And in the zone that is circled in red, I cannot select anything else that my 64GB USB key, there is no other option.

Any other idea? :( Thanks a lot

---

### Post by sudodus on 2017-10-30
Am I right, that the installer does not 'want to' install into the internal drive and goes directly to your USB pendrive?

Which mode are you booting into (UEFI or BIOS), and is the internal drive prepared for that mode?

---

### Post by nathanlcht on 2017-10-30
Indeed, I never have the choice, I have never seen my internal drive in the list, it is always the USB key. 

I just followed the tutorial, so when I reboot I press the option key and then I have the choice between OS X and EFI Boot, and I click the last one which gets me to the menu "Try ubuntu, Install ubuntu..".  As to the partition, the "boot loader" one is OS X Extended (journaled) and the tutorial said the format of the one for Ubuntu (which I set at 50GB) doesn't matter as it will be changed later. So I also put it OS X Extended (journaled). Is that what you wanted to know?

---

### Post by oldfred on 2017-10-30
You said you partitioned HD, your internal drive?
If so then there is nothing along side to install into, you only use Something Else as you already created partitions.

I have seen some comments on Macs that it is best to dual boot or keep the Mac install as there are a few system things that can only be done from the Mac and not from Linux.

---

### Post by nathanlcht on 2017-10-30
Well, I partitioned Apple SSD which is now divided into Macintosh HD (the original one), Ubuntu HD and Ubuntu Boot Loader. 

And as I said, I can never select Something Else, I just have the second screen where I have to partition my USB key (64GB or free space) instead of selecting the partition I just created. 

Yes, in this case I need really need Linux because there are more and more things that I can't do or that are more complicated on OS X but that I need for school projects.

---

### Post by sudodus on 2017-10-30
When booted from the USB pendrive, please run the following commands and post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

Commands:

```

df
sudo parted -ls
sudo lsblk -f
sudo lsblk -m

```

---

### Post by nathanlcht on 2017-10-30
There it is.

```

ubuntu@ubuntu:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
udev             4001860       0   4001860   0% /dev
tmpfs             803580    9628    793952   2% /run
/dev/sda         1550400 1550400         0 100% /cdrom
/dev/loop0       1496320 1496320         0 100% /rofs
aufs             4017896    4744   4013152   1% /
tmpfs            4017896     172   4017724   1% /dev/shm
tmpfs               5120       4      5116   1% /run/lock
tmpfs            4017896       0   4017896   0% /sys/fs/cgroup
tmpfs            4017896     132   4017764   1% /tmp
tmpfs             803580      84    803496   1% /run/user/999
ubuntu@ubuntu:~$ sudo parted -ls
Error: The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Model: General USB Flash Disk (scsi)
Disk /dev/sda: 64.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: pmbr_boot

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB                EFI System Partition  boot, esp
 2      211MB   64.5GB  64.3GB                                     msftdata


ubuntu@ubuntu:~$ sudo lsblk -f
NAME   FSTYPE  LABEL             UUID                                 MOUNTPOINT
loop0  squashf                                                        /rofs
sda    iso9660 Ubuntu 16.04.3 LTS amd64
&#9474;                                2017-08-01-11-51-33-00               /cdrom
&#9500;&#9472;sda2 vfat    Ubuntu 16.04.3 LTS amd64
&#9474;                                398E-230F                            
&#9492;&#9472;sda1 iso9660 Ubuntu 16.04.3 LTS amd64
                                 2017-08-01-11-51-33-00               
ubuntu@ubuntu:~$ sudo lsblk -m
NAME    SIZE OWNER GROUP MODE
loop0   1.4G root  disk  brw-rw----
sda    60.1G root  disk  brw-rw----
&#9500;&#9472;sda2  2.3M root  disk  brw-rw----
&#9492;&#9472;sda1  1.5G root  disk  brw-rw----

```

---

### Post by sudodus on 2017-10-30
These command line tools cannot find your internal drive. What happened to it?

I guess that the installer has the same problem, it does not find the internal drive.

---

### Post by C.S.Cameron on 2017-10-30
Ubuntu can be installed to the pendrive it was booted from.
[https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from](https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from)

---

