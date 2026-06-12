---
title: "How To: Ubuntu Portable"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by wcbardwell on 2007-06-04
I know when I first started using Ubuntu, I didn't want to install it onto my Hard Drive (For fear that I wouldn't like it), so I decided to try to install it on my 120GB USB-powered portable Hard Drive... This is how I did it:

Starting with my machine off (and ubuntu disk in the cd tray), I connected my HDD and a 1 GB flash drive to my PC.
Next, I turned on the machine and booted from the cd.
After everything is booted, I entered:
```
sudo fdisk -l
```
It gave me the list of HDD attached to the machine. I wrote down the drive letter for the 120GB HDD (sdb on mine)
I proceeded to install at wiped the 120GB disk clean for a full-ubuntu drive.
Before clicking the final "install," I changed the address for grub to the drive letter (sdb on my machine).
Then I allowed it to install.
Once installation was complete, I rebooted (making sure to remove the 1GB flash drive and the disc from the tray first).
Once GRUB came up, I received an error.
After restarting the machine a few times, I finally got the GRUB menu up and running (but still not loading).
In the menu, I presses "e" to edit the booting HDD for ubuntu (I changed it from (1,0) to (0,0) ) and pressed "b."
After getting the machine to boot, I went in and edited the menu.lst file:
```
sudo gedit /boot/grub/menu.lst
```
I scrolled down and changed the drive that all of the options on the bootloader boots from ( from HDD (1,0) to (0,0) )
I saved the file and restarted.

Now I have a portable HDD that I take with me everywhere and use ubuntu on practically any PC. I have run into some problems reconfiguring X on some nvidia machines, but it's not a big deal to me. Hope this quick run-through helps someone.

**NOTE**
In order to boot from this drive, you need to either select it from the boot menu on the machine or change the boot order in the setup screen on your computer so that the USB drive comes before the internal (a prompt upon restart will tell you what button to push for boot/setup menus).

---

### Post by Dylnuge on 2007-06-04
Nice guide. Thanks!

---

### Post by gene74 on 2007-06-05
i am trying to do this also but kept having some problems with partition. i have a 30 gb hd in a usb external case that i want to use. how do i partition it?


nvm i got it to work

---

