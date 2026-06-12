---
title: "Help: getting Ubuntu to run on an SD card"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by Watchtow3r on 2007-12-18
I've been trying to get Ubuntu to run on my SD card using [this]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") tutorial. I was substituting in mmcblk0 for the sdx part, because my drive wasn't listed as sda1 or anything like that. Also, in step 6, it said :Type umount /dev/sdx1. I tried entering this in: umount /dev/mmcblk0p1 because I think that's the first partition (I used it in later steps) but it didn't work, so I just entered in umount /dev/mmcblk0 and it worked. Besides that one step, I did everything else the same. Now, I think I did everything right, but here's my problem: It wouldn't load when I restarted my computer, so I tried changing boot order. All of the devices besides something marked something like !Network Adapter or Network Adapter! were placed above the hard drive. It still wouldn't, so I read the note at the bottom of the page. It said this: Note: If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type sudo apt-get install lilo then type lilo -M /dev/sdx (replacing x with the letter of your flash device). I typed sudo apt-get install lilo, but I got this message:

LILO configuration                                                        &#9474;  

 &#9474;                                                                           &#9474;  

 &#9474; It seems to be your first LILO installation. It is absolutely necessary   &#9474;  

 &#9474; to run liloconfig(8) when you complete this process and execute           &#9474;  

 &#9474; /sbin/lilo after this.                                                    &#9474;  

 &#9474;                                                                           &#9474;  

 &#9474; LILO won't work if you don't do this. 

I hit OK, and then typed lilo -M /dev/mmcblk0 but got a not a master device with a primary parition table message. I tried mmcblk but got a No such file or directory message. I then thought the problem was that I hadn't run the liloconfig(8) thing, but got a bash: syntax error near unexpected token `8' message. I then tried just liloconfig, but got a 
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "config": could not write /var/cache/debconf/config.dat-new: Permission denied message. I'm just gonna cut and paste my whole thing with terminal so you can see what I was trying to do. I tried running fdisk to make sure I was entering the right disk name.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 388kB of archives.
After unpacking 1253kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main mbr 1.1.9-2ubuntu4 [23.2kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main lilo 1:22.8-3ubuntu4 [364kB]
Fetched 388kB in 1s (198kB/s)
Preconfiguring packages ...
Selecting previously deselected package mbr.
(Reading database ... 92004 files and directories currently installed.)
Unpacking mbr (from .../mbr_1.1.9-2ubuntu4_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-3ubuntu4_i386.deb) ...
Setting up mbr (1.1.9-2ubuntu4) ...
Setting up lilo (1:22.8-3ubuntu4) ...

ubuntu@ubuntu:~$ lilo -M/dev/mmcblk0
Fatal: /dev/mmcblk0 is not a master device with a primary parition table
ubuntu@ubuntu:~$ lilo -M/dev/mmcblk
Fatal: Cannot open /dev/mmcblk: No such file or directory
ubuntu@ubuntu:~$ lilo -M/dev/mmcblk0p
Fatal: Cannot open /dev/mmcblk0p: No such file or directory
ubuntu@ubuntu:~$ fdisk -l

Disk /dev/mmcblk0: 2032 MB, 2032664576 bytes
4 heads, 16 sectors/track, 62032 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x6f20736b

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1       22889      732440    6  FAT16
/dev/mmcblk0p2           22890       62032     1252576   83  Linux
ubuntu@ubuntu:~$ lilo -M/dev/mmcblk0
Fatal: /dev/mmcblk0 is not a master device with a primary parition table
ubuntu@ubuntu:~$ lilo -M/dev/mmcblk
Fatal: Cannot open /dev/mmcblk: No such file or directory
ubuntu@ubuntu:~$ liloconfig(8)
bash: syntax error near unexpected token `8'
ubuntu@ubuntu:~$ liloconfig
debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
debconf: DbDriver "config": could not write /var/cache/debconf/config.dat-new: Permission denied
ubuntu@ubuntu:~$ 


Can someone please help me? Thanks. Also, please be very simple and tell me the exact commands to enter please, I'm very new with ubuntu.

---

### Post by wormser on 2007-12-18
That tutorial is for booting off of USB not SD.  I am not aware of being able to boot off of SD .  Boot into your BIOS, check the boot order and see if SD is an option.  You can buy a 1 gig usb drive for about $10.

> USB Ubuntu 7.10 Essentials:

    * Ubuntu7.10 ISO
    * CD Burner
    * 1GB USB flash drive (2GB+ recommended)
    * U710fix.tar


---

### Post by Watchtow3r on 2007-12-18
Well I have all this stuff in the terminal now and I don't really want to close it. Shouldn't I still be able to be able to load the lilo thing and everything even if it technically can't boot in my computer?

and btw my computer does have an option to put a USB hard drive ahead of the internal hard drive in the boot order. What does the computer care whether it's a hard drive or an SD card?

---

### Post by wormser on 2007-12-18
> **Watchtow3r said:**
> Well I have all this stuff in the terminal now and I don't really want to close it. Shouldn't I still be able to be able to load the lilo thing and everything even if it technically can't boot in my computer?

and btw my computer does have an option to put a USB hard drive ahead of the internal hard drive in the boot order. What does the computer care whether it's a hard drive or an SD card?

USB is different than SD.  Go and buy a 2 gig USB thumb drive like the tutorial recommends.  Then follow the guide and have USB as the number one boot item.

I have no idea what is on your terminal, but it sounds like you have not installed lilo yet.  I would not install it.  Are you running Ubuntu from your hard drive right now.  If so, Ubuntu installs Grub by default and not lilo.  Both are boot managers.  You are better off sticking with Grub.

---

### Post by anaconda on 2007-12-18
actually.. some (most?) usb-SD readers work exactly the same than USB-thumb drives.  So it should work.

I once had DamnSmallLinux booting from a CF-card..

---

### Post by Watchtow3r on 2007-12-18
in that case, do you have any idea how i can do the lilo -M /dev/sdx command (from the note  on the last part of [this]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") page to make ubuntu load when I boot up my computer? thanks.

---

### Post by Watchtow3r on 2007-12-18
Ignoring the fact that I'm using an SD card, can someone help me install that lilo thing, and tell me why it's not working? thank you.

---

### Post by vrix on 2007-12-18
```
ubuntu@ubuntu:~$ lilo -M/dev/mmcblk0
Fatal: /dev/mmcblk0 is not a master device with a primary parition table
ubuntu@ubuntu:~$ lilo -M/dev/mmcblk
Fatal: Cannot open /dev/mmcblk: No such file or directory
ubuntu@ubuntu:~$ lilo -M/dev/mmcblk0p
Fatal: Cannot open /dev/mmcblk0p: No such file or directory
ubuntu@ubuntu:~$ fdisk -l

Disk /dev/mmcblk0: 2032 MB, 2032664576 bytes
4 heads, 16 sectors/track, 62032 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0x6f20736b

Device Boot Start End Blocks Id System
/dev/mmcblk0p1 * 1 22889 732440 6 FAT16
/dev/mmcblk0p2 22890 62032 1252576 83 Linux
```

greetings!

I think you should type /dev/mmcblk0p1 instead of mmcblk as indicated in your Device Boot Start End Blocks Id System like this: ```
$lilo -M /dev/mmcblk0p1
``` Pls. take note of the space between -M and /dev/...

---

### Post by Frog-jump on 2008-07-14
CLUES :

[http://www.a110wiki.de/wiki/Booting_from_SD](http://www.a110wiki.de/wiki/Booting_from_SD)

It seems that it is a bootloader problem. For me grub.
After boot from hda, the SD/MMC is well recognised.
if I type : root ( TAB
grub only lists fd0 and hd0

Someone also said that it must be FAT32 because of issues with SD v2.0

And I found mmcblk patches for grub2 but not grub
[http://merges.ubuntu.com/g/grub2/grub2_1.96+20080704-2.patch](http://merges.ubuntu.com/g/grub2/grub2_1.96+20080704-2.patch)

but Ubuntu does not use grub 2 !

P.S. To WORMSER : 1/ Your comment is definitely not helpful
2/ It also shows that you understand nothing to the problem

---

