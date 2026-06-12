---
title: "Macbook 2.1 and lubuntu 19.10"
date: 2019-12-26
forum: Apple Hardware Users
---

### Post by ivaldis6 on 2019-12-26
I am trying to install Lubuntu 19.10 onto a macbook 2.1. I have been unsuccessful with having the laptop find my boot USB by pressing the "option" button on startup, it is also not appearing in the bootable disks in the mac settings.  I have tried both 64 and 32 bit versions created by etcher on my windows machines. I have also tried creating the install USB's on the mac using terminal with no success.  
I finally removed the HDD from the laptop and plugged it into a spare windows machine and installed Lubuntu 19.10 64bit on to the drive that way.  Now that it is back in the macbook all i get is a flashing folder icon with a question mark in it.  I am not worried about recovering any of OSX as it is not updating.  

How can I get a lightweight distro to run on this computer?

solved

---

### Post by howefield on 2019-12-26
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by ivaldis6 on 2020-01-03
[https://www.linux.com/tutorials/how-rescue-non-booting-grub-2-linux/](https://www.linux.com/tutorials/how-rescue-non-booting-grub-2-linux/)


To  start I removed the HDD and plugged it into a windows machine and  installed Lubuntu with a regular bootable USB as the MacBook wasnt  recognizing it. 
I manually partitioned it as described by "https://forums.linuxmint.com/viewtopic.php?t=137865"
Number  Start   End     Size    File system     Name  Flags
 5      1049kB  10,5MB  9437kB                        bios_grub
 1      10,5MB  99,6MB  89,1MB  fat32                 boot
 2      99,6MB  12,1GB  12,0GB  ext4
 3      12,1GB  16,1GB  4000MB  linux-swap(v1)
 4      16,1GB  120GB   104GB   ext4

The MacBook would not recognize the HDD so I created a GRUB rescue USB following the instructions from the following two websites: 
"https://www.redips.net/linux/create-fat32-usb-drive/"
"https://www.linux.com/tutorials/how-rescue-non-booting-grub-2-linux/"
I was able to use the GRUB rescue USB to get to the functional operating system using the following commands:
grub> set root=(hd0,1)                                       <-I used my primary partition which ended up being (hd1,2)
grub> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda1   <-My kernel version was different and my root was /dev/sda2
grub> initrd /boot/initrd.img-3.13.0-29-generic              <-Kernel versions need to match
grub> boot                                                   <-boots the system

I then tried to fix the boot in terminal by using 
sudo update-grub
sudo grub-install /dev/sda

This didn't fix the issue, I could still only boot from my GRUB rescue USB.  I went back to [https://forums.linuxmint.com/viewtopic.php?t=137865](https://forums.linuxmint.com/viewtopic.php?t=137865).
I attempted to force the install of grub with:

sudo mount /dev/sda1 /mnt
sudo grub-install --recheck --force --boot-directory=/mnt /dev/sda2

After those commands were entered I rebooted and the laptop booted to "grub rescue>" without the usb.  
set root=(hd0,2)                <-My partition happened to match, but check using "ls"
set prefix=(hd0,2)/boot/grub    <-The partition should match the root
insmod normal                   <-At this command I was missing 2 files and was notified one at a time, so I got to do the following steps twice
(reboot using GRUB rescue USB) I copied the containg folder from my primary laptop to the MacBook.  

Once both files were on the macbook, it booted up to Lubuntu straight away, no stopping to choose any other OS's.

---

