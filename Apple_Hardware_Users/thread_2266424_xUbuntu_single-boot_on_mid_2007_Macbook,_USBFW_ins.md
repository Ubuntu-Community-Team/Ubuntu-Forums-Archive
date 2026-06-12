---
title: "xUbuntu single-boot on mid 2007 Macbook, USB/FW install, no REfit/Refind"
date: 2015-02-22
forum: Apple Hardware Users
---

### Post by bionicman2 on 2015-02-22
**Preliminary remark:**

Yesterday I finally succeeded to get xUbuntu 14.04 32bit running on my white 13" Macbook (mid 2007; model "2,1") as single-boot (actually all other 32bit Ubuntu-like versions should also work fine!). The whole experiment started two weeks ago and I spent countless hours to acomplish this task. Consequently, I wrote down a step-by-step guide to enable others who struggle in a similar way. Here should also be mentioned that **there are many guides out there which try to explain the installation but I never found a coherent one which applied to my Macbook**: some of them are either (i) Refind/Refit-based (which didn't work for me), (ii) target a multi-boot installation (I dont' want that), (iii) cover the installation of a 64bit OS version (did not work), (iv) refer to a DVD/CD-based installation (I don't have an optical drive anymore) or (v) refer to a newer Macbook model which already has a 64 bit EFI.

**Why to switch from OS X to Linux?**

Then, of course, why should someone switch from OS X to Linux, because the Macbook is perfectly optimized for OS X, isn't it? 
Well, even though this Macbook model already has an x86 Intel processor, its 32bit EFI restricts the installation of OS X versions above Lion (to the best of my knowledge...). Moreover, the hardware is too limited for current OS X versions such as Yosemite. Third, I do not won't to be locked in to the Apple universe anymore. Some time ago, I already migrated all my data to my personal owncloud, and so got totally rid of any 3rd party cloud services such as iCloud.

**Why no Refind/Refit?**

Short answer: it did not work at all on my machine. Maybe I did something different as I should have in the first place, but I tried several variants that all included Refit/Refind but all of them ended in a non-bootable system.

**Did I modify/upgraded my Macbook?**

The most important change is, that I don't have any optical drive anymore (replaced it by a 2nd HDD/SDD slot) and was thus forced to install via USB or Firewire.
Besides, I upgraded to 4GB of RAM (to the best of my knowledge, more RAM isn't supported on that system).

**What Linux operating system did you choose and why?**

I chose xUbuntu because I wanted to have a Debian-based system and Xubuntu also comes with Xfce, which is a stable, light and configurable desktop environment.
You can get it here: [http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/xubuntu/releases/14.04/release/xubuntu-14.04.2-desktop-i386.iso](http://ftp.uni-kl.de/pub/linux/ubuntu-dvd/xubuntu/releases/14.04/release/xubuntu-14.04.2-desktop-i386.iso)

[HR][/HR]
**Checklist (before you start anything):**


[LIST=1]
[*]BACKUP, BACKUP, BACKUP your data! Before formatting/erasing your disks to install the new operating system, you should backup all your data to a safe location. 
[*]If you are not sure about how to work on the command line or how to check the partitioning of your hard drive, you should better not take any risk. 
[*]Take your time. Even though this installation succeeded for me in less than 30 minutes (once I figured how to do it), the new OS needs to be configured. That is, if you need to work on the computer on a daily basis, you should better get a second laptop in case the installation/configuration takes longer than expected! 
[*]You need to have an image of Snow Leopard or Lion mounted on a partition of an external Firewire (?) hardisk because this allows you to (i) reinstall OS X at any point in time and (ii) to conduct several maintenance operations. Moreover, this external hardisk allows you to prepare an extra partition with the Ubuntu image which would additionally speed up the installation process (compared to the USB stick). 
[/LIST]
 
[HR][/HR]
**Step-by-step guide:**

**Part 1:**


[LIST=1]
[*]Preparing the USB pendrive (a 2GB drive is optimal, but even a 1GB one is ok as long as the Linux image file is small enough, i.e., smaller than 970MB) 
[*]Format the pendrive either in OS X disk utility with FAT32 file system or use Gparted on a another linux machine. 
[*]On the pendrive, create a folder "EFI" and in that folder create a subfolder named "BOOT". 
[*]Download 32bit version of xUbuntu from the above link, rename the file to "boot.iso" and copy it the the folder "BOOT" on your pendrive. 
[*]Download the "Mac Linux USB loader" archive from Github: [https://github.com/SevenBits/Mac-Linux-USB-Loader/archive/v1.1.zip](https://github.com/SevenBits/Mac-Linux-USB-Loader/archive/v1.1.zip)
[LIST]
[*]Note: I used v1.1 but you could try to use a recent one from SevenBits Github page 
[/LIST]
  
[*]Extract the archive and copy the file "bootIA32.efi" from the folder "EFI Loader" to the folder "BOOT" on your pendrive. 
[*]**Summary:** your pendrive should now contain the folder "/EFI/BOOT" and therein the two files "boot.iso" and "bootIA32.efi" should be located. 
[*]If you have a Firewire external HDD you can also create a FAT32-formatted 2GB Partition on it and apply the previous steps. If you later boot from the external HDD, it is most likely faster compared to the USB install. 
[/LIST]

**Part 2:**


[LIST=1]
[*]Plug-in either your pendrive or Firewire HDD and start your Macbook. Hold down the ALT-key to show the EFI boot menu at startup. An orange drive icon named "EFI BOOT" should show up (this is your Ubuntu install medium!!). Select it! 
[*]Ubuntu now loads the image and creates a ramdisk. After one minute or so the Ubuntu OS should have been booted. Note: If you encounter an initramfs-related problem during the startup, you should prepare your pendrive according to part1 again. I encountered this problem once which might be related to some copy and delete operations I conducted on that pendrive which in turn might have somehow confused the initramfs process. To be clear: just format the pendrive according to the above steps, only create the folders and copy the two files in there. Do not delete the image file on the pendrive and replace it by other versions because this might result in the initramfs problem. 
[*]Open a terminal and start the partition manager via "sudo gparted" 
[*]Select your internal harddrive (not the external one!!) where you want to install Ubuntu to (usually /dev/sda) and remove all existing partitions, including the hitherto OS X EFI boot partition. Finally, you should have a single entry "unallocated space" with the size of your harddisk. 
[*]Start the Ubuntu installation wizard by selecting the icon on the desktop. Once the wizard asks you were to install the new OS, select the "use entire harddisk from the top" and make sure that the correct hard drive is selected. 
[*]At some point during the installation, the wizard will complain about not being able to install the boot loader. For me, this message was NORMAL and ALWAYS appeared. Just check "continue without bootloader / install bootloader manually". 
[*]Once the installation has finished, select "Continue testing"
[LIST]
[*]Note: in case you accidentally restarted your computer, the new Ubuntu won't boot (we don't have a bootloader installed yet) and you need to boot from either your pendrive or external harddisk again. 
[/LIST]
     
[/LIST]
[B]
Part 3:[/B]


[LIST=1]
[*]You are still in the Ubuntu OS (as booted from e.g. the pendrive). Now open a terminal window from the start menu. 
[*]Install the grub manager for 32bit EFI systems:
[LIST]
[*]     ```
sudo apt-get install grub-efi
``` 
[*]     This will install the package "grub-efi-ia32" as required for the manual bootloader installation. 
[/LIST]
  
[*]Run "sudo fdisk -l" to find out which one of your partitions is marked with the "boot" flag (marked by an asterisk). This should normally be /dev/sda2 
[*]Mount the partition /dev/sda2 to /mnt:
[LIST]
[*]```
 sudo mount /dev/sda2 /mnt
``` 
[/LIST]
  
[*]Also mount relevant system dirs from your current live Ubunutu session to /mnt
[LIST]
[*]```
 for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
``` 
[*] Note: the "-B" parameter remounts a subtree to /mnt but also keeps its contents available at the original destination 
[*]Credits: I got this hint from reply #63 in this thread: [1] 
[/LIST]
  
[*]Set the base/root directory for all subsequent commands to "/mnt":
[LIST]
[*]```
sudo chroot /mnt
``` 
[/LIST]
  
[*]Install grub. It should finish with "Installation finished. No errors reported."
[LIST]
[*]```
grub-install --recheck --no-floppy --root-directory=/ /dev/sda
``` 
[/LIST]
  
[*]Finally, update grub in order to properly detect the newly installed Ubuntu OS:
[LIST]
[*]```
update-grub
``` 
[/LIST]
                     
[/LIST]

**Part 4:**


[LIST=1]
[*]Restart you laptop. Hold down the ALT key and boot from the Snow Leopard image. Do not install Snow Leopard again but instead start a terminal window from the menu bar (entry "utilities") and issue the following 'bless' command. It tells the Mac to boot in BIOS mode rather than attempting a normal EFI boot.
[LIST]
[*]```
bless --device /dev/disk0s1 --setBoot --legacy --verbose
``` 
[*]Note: /dev/disk0s1 is the boot partition where grub should be located 
[*]Credits: [2] 
[/LIST]
  
[*]Restart the computer and do not press anything! Since we blessed the boot partition it should now run in legacy BIOS mode and after some seconds the grub boot menu should show up. In case you only have one OS installed, the GRUB menu might probably not show up and directly boot the newly installed Ubuntu system. The only downside is that from the restart of the computer to Ubuntu login took around 90 seconds on my computer. This might be due to the BIOS emulation and/or a non-optimized grub configuration. 
[*]Use your new OS and enjoy the freedom of having free updates for a long time and other advantages such as not being locked in to a proprietary OS/hardware. 
[/LIST]
 
[HR][/HR][B]
Remapping buttons on you Macbook keyboard[/B]:

Ok, there are two basic tools you need to use on the terminal. The first one is "xev" which shows you the keycode for every button pressed. That said, press the buttons you want to remap and write down the keycode. The second one is the program "xmodmap". If you issue the command "xmodmap -pke > xmodmap.current.mapping" you will get a full list of all current mappings. This file holds 6 mappings for each keycode depending on which modifier buttons you have pressed. More info is found at link [3]. My final changes are as follows and I wrote them to the file "~/.Xmodmap" which is loaded via the command "xmodmap ~/.Xmodmap":

[FONT=courier new]! swap the command and control keys (both left and right)
clear control
clear mod4
keycode 105 =
keycode 206 =
keycode 133 = Control_L NoSymbol Control_L
keycode 134 = Control_R NoSymbol Control_R
keycode 37 = Super_L NoSymbol Super_L
add control = Control_L
add control = Control_R
add mod4 = Super_L

! map "[" to ALT-5
keycode  14 = 5 percent 5 percent bracketleft threeeighths

! map "]" to ALT-6
keycode  15 = 6 ampersand 6 asciicircum bracketright fiveeighths

! map "|" to ALT-7  AND "\" to Alt-Shift-7
keycode  16 = 7 slash 7 ampersand bar backslash

! map "{" to ALT-8
keycode  17 = 8 parenleft 8 asterisk braceleft trademark

! map "}" to ALT-9
keycode  18 = 9 parenright 9 parenleft braceright plusminus

! map "@" to ALT-L
keycode  46 = l L l L at Lstroke

! map "~" to ALT-N
keycode  57 = n N n N asciitilde rightsinglequotemark[/FONT][B]



Problems still to solve:[/B]



[LIST=1]
[*]As said before, you might need to further tune your grub config to reduce the startup time. Modify the GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub to include reboot=cold. The modified line should then read GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=cold". Issue the "update-grub" afterwards. This hint was found here [2].
[*]Suspend isn't working atm. Whenever I close the Macbook and open it again, the screen stays black and the GUI won't show up again. Reboot is then required. Thus, I changed in the energy settings, to not go to standby at all but to rather shutdown the Macbook if the power is < 5%. I guess this a fair solution (I mostly have the power cable plugged in) until I figure out how to solve this problem because. 
[/LIST]
[B]
Links:[/B]

[1] [HTML]http://forum.peppermintos.com/index.php?topic=1050.60[/HTML]
[2] [HTML]http://www.geek-tips.com/2013/03/09/install-linux-mint-on-a-mac-mini-2-1/[/HTML]
[3] [HTML]https://wiki.archlinux.org/index.php/xmodmap[/HTML]

---

### Post by pallisvans on 2016-02-02
Thank you so much for this! After 3 days of trying to install Elementary Os on my Mac Mini (mid 2007) this finally brought it home :) What was missing for me was how to install the bootloader, your instructions worked like charm. Thanks again!

---

### Post by h1cloud on 2016-07-24
I also installed Xubuntu on my Macbook (white late 2008, core 2 duo, 2GB Ram), but there are overheating issues (heavy fan activity). Did You also experience overheating and if yes, how could I get rid of it? 

I agree in every point to change OS, looking desperately for an alternative to OSX :-/

---

### Post by howefield on 2016-07-24
Thread closed.

OP hasn't been back in a year and a half, so probably best to start a new thread referencing this one if need be.

---

