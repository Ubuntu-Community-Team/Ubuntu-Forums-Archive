---
title: "Ubuntu on macbook without the MacOSX"
date: 2009-11-15
forum: Apple Hardware Users
---

### Post by aprigiosimoes on 2009-11-15
Hi All;

Someone has 9.x installed Ubuntu on macbook without the Mac OS X installed? It detected the hardware as well? Efi boot with grub? Sound? wireless card and shutdown the machine?

I will not use or refit and bootcamp to dual boot but the entire machine dedicated to Ubuntu.

Thank you.

---

### Post by h00ver on 2009-11-16
Successfully installed Ubuntu 9.10 Desktop 64bit only on my MacBook 2.1 (Late 2006).

[Single-Boot Instructions]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation")
[Enable all features on MacBook 2.1]("https://help.ubuntu.com/community/MacBook2-1/Karmic")
[How to single boot Linux without delay on Macbook]("http://ubuntuforums.org/showpost.php?p=5166788&postcount=21")

---

### Post by aprigiosimoes on 2009-11-16
And the question of grub2? I saw the site [http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook), it works normally with the EFI.Vc had some problems? Apple computer I found the best place for a good Linux. Very Good!

Tanks.

---

### Post by aprigiosimoes on 2009-11-16
Hi;

My question is for the macbooks with intel processors, preferably the new,with GPU from Nvidia.

tanks;

---

### Post by katejones on 2010-03-09
Macbook 2.1 with Ubuntu 9.10 (only Ubuntu on the disk, nothing else, no MacOSX).
Wireless, touchpad, sound etc - everything is all working great.

Only problem is a 20second delay at start up (which I'm hoping to fix with the help of this forum)

---

### Post by Dullstar on 2010-03-11
> **aprigiosimoes said:**
> Hi All;

Someone has 9.x installed Ubuntu on macbook without the Mac OS X installed? It detected the hardware as well? Efi boot with grub? Sound? wireless card and shutdown the machine?

I will not use or refit and bootcamp to dual boot but the entire machine dedicated to Ubuntu.

Thank you.

The only thing I have found so far that doesn't work is the sound and rebooting - at least it doesn't seem to from the CD.   You can still shut down though.  Of course, I do still have OS X on but that wouldn't change how well Ubuntu would detect the hardware.  I am not aware of any way to boot Linux successfully from a Mac without rEFIt, although it can probably be done.

With 9.04, anyways.  9.10 is too buggy for me to put on my nice iMac in my opinion. ;)

---

### Post by katejones on 2010-03-11
9.10 - sound and rebooting on my macbook 2.1 (without anything else installed) definitely are working fine.

It's only the boot-up delay that I've found somewhat ' malfunctioning' (but it still boots faster than Vista ;) )
Shutdown is within seconds.
I think Ubuntu definitely is an improvement over Max OSX too, much faster, and (being a Windows user originally) I love that I can used the ctrl key like I do on windows again.
Also with Ubuntu installed (following the Touchpad options settings thingie in the wiki) I can now use the touchpad itself to rightclick (use two fingers on the touchpad, and click the bar underneath), where before on OSX I had to use 2 hands. (call this pianist lazy..)

Wireless was working out of the box too (including Airport).

For sound: if you are using headphones they seem to be muted by default, you have to run ' alsamixer'  in the Terminal and unmute them. (the speakers at the right were my headphones here)

---

### Post by aprigiosimoes on 2010-11-20
Yes;
I use Macbook and macmini with Ubuntu in single install

For reboot and shutdown, add in grub 

reboot=pci

---

