---
title: "slow boot to grub"
date: 2011-04-11
forum: Apple Hardware Users
---

### Post by afrodocter on 2011-04-11
i have a macbook pro 3,1 and installed a single-boot ubuntu, and then blessed the drive using a mac cd. 

however, the efi/bios boot stage still takes a long time (like 15s) to even get to grub. after this the laptop boots in like 5s.

has anyone experienced this? and know a way to fix this?

thanks

---

### Post by handy on 2011-04-25
You can change the grub timeout parameter like so:

**sudo gedit /boot/grub/grub.cfg**

Look down a ways in the file & you will find the following:

**timeout=10**

Change it to a lower number & see if that helps you.

Good luck. :)

---

### Post by handy on 2011-04-25
This info may be of some help too:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Avoid%20long%20EFI%20wait%20before%20GRUB](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Avoid%20long%20EFI%20wait%20before%20GRUB)

---

### Post by mulbric3 on 2011-11-20
I've got the same problem and same MBP model.

Even though I use an SSD, the total boot time from pushing button to Desktop is 50s. (in Lion it was 27s)

The time till the grub menu appears seems a bit much. Does it have to to with the MBP first loading the EFI then the Kernel and Grub?

The timeout is already set to 0s and the neccessary files have been compiled.

---

