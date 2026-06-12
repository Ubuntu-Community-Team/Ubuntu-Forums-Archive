---
title: "Grub Hangs with triple boot... anyone else?"
date: 2009-08-25
forum: Apple Hardware Users
---

### Post by joshua05 on 2009-08-25
Here's the story... (Mactel 5,5)

Installed OS X, installed Windows 7, installed Jaunty, latest updates.  No Bootcamp.

Installed Refit to select which OS at startup.  On startup, selecting either windows or linux takes me to the same grub menu (that's fine I don't care).

After working in Linux and Windows for a while, I decided to switch back over to OS X.  After using OS X, restarting, Grub now hangs when selecting either Windows or Linux: "Grub loading stage 2..."  WHAT DID OS X DO!?!?!

After doing a fresh triple boot install, everything works fine and boots correctly UNTIL I boot into OS X.  (Which causes my grub to hang)  Maybe OS X is mounting something poorly?

I keep trying to reinstall grub, but the problem is I can't get to my boot partition (ext2, 100mb).

When I'm on the LiveCD, this is what happens:
root@ubuntu:~# mount /dev/sda6 /media/root/
root@ubuntu:~# mount /dev/sda4 /media/root/boot
root@ubuntu:~# ls /media/root/boot/
ls: reading directory /media/root/boot/: Input/output error

My Partition Table:
sda1: Mac GPT
sda2: HFS+ for Mac OS
sda3: NTFS Windows
sda4: ext2 /boot
sda5: swap
sda6: ext4 /

Any ideas?

---

### Post by joshua05 on 2009-08-26
And... solved the problem (of OS X Leopard making Grub Hang).

If you have a Mactel 5,5, and you want to tri-boot Jaunty, Windows and OSX, you may encounter problems with Grub.  (It doesn't play well with Leopard)

The approach is to use Refit with Lilo as a bootloader instead of Refit & Grub.

To install Lilo, Grab the Ubuntu Alternate-Install CD (which is a really fast torrent download).  Launch the install, go through all the prompts until the end, when it asks you where to install Grub.  At this point navigate to the "Go Back" button.  

On the menu that pops up, hit "Install Lilo."

Select the option to Install Lilo to the MBR.  With Leopard, Apple's GUI'd bootloader is insulated from any changes to the MBR, so don't worry.

If your used to Grub, switching to Lilo is simple.  (I don't like Lilo as much, but hey... it doesn't break on me.)

Grub's /boot/grub/menu.lst is just like lilo's /etc/lilo.conf.  After you makes changes to lilo.conf, be sure to run /sbin/lilo to commit your changes to the bootloader.

I am now successfully tri-booting!

---

