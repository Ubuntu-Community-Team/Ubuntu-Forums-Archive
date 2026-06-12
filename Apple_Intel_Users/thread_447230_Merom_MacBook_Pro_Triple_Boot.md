---
title: "Merom MacBook Pro Triple Boot"
date: 2007-05-17
forum: Apple Intel Users
---

### Post by Twinaxx on 2007-05-17
Hi guys, 
I'm looking to make my notebook a triple booter. I've tried following the wiki from onmac, but the Ubuntu installer starts freaking out when i try to install without a swap volume. According to the guide it should let me go ahead with just a warning, but for me its a no go.


A little info about my machine:

Core 2 Duo MacBook Pro, 2GB RAM.
I have rEFIt already running, and I am trying to install Ubuntu 64-Bit, along with Mac OS X. Vista will be installed in the next few days.


Any suggestions would be appreciated.

Cheers!

---

### Post by ronocdh on 2007-05-18
Are you using Feisty 64-bit? IIRC Edgy threw a fit about the swap space, but Feisty is a bit more submissive. You could also try installing from the alternate CD.

---

### Post by andrego on 2007-05-18
Strange.  I have the same hardware (MBP C2D, 2GB Ram) and can confirm that Ubuntu 7.04 64-bit installed fine.  I did get the warning about no swap space you mentioned, but it was just a dialog box that I could click past.

When I got the system, just installed bootcamp, partitioned my drive, and threw in my Feisty cd.  Didn't do anything fancy or special.  Install just went fine, including GRUB (which failed in Dapper and Edgy).

If you're using a Feisty CD it should work for you as well.  Both 32-bit and 64-bit tested fine.  Wish I could be more help...

Edit: Perhaps adding a swap file before install could help.  If you can boot the LiveCD fine, use the following command to create one before the install.

For reference, I used [this link]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp") for triple boot, and to create a swap file (since the MacBook uses EFI, which uses 1 primary partition, and Bootcamp require Windows be on the last Primary partition, and Mac OS X and Linux clearly each need one as well, you won't be able to make a swap partition).

The only important commands in that article are:
1) Cutting your MacOS X drive into three parts.
sudo diskutil resizeVolume disk0s2 60G "Linux" "Linux" 17G "MS-DOS FAT32" "Windows" 15G
(Note: Change 60G, 17G, and 15G to sizes you desire, which if added together should equal the total size of your HD, which is likely 120GB if you have the 15" MBP like me)

2) Creating a swap file once you reboot after the install
dd if=/dev/zero of=/swap bs=1024 count=1048576
mkswap /swap
swapon /swap
chmod 600 /swap
(Note, make sure to update /etc/fstab to mount your swap automatically upon reboot)

---

