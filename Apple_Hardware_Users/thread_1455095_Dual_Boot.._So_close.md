---
title: "Dual Boot.. So close"
date: 2010-04-15
forum: Apple Hardware Users
---

### Post by Soupy on 2010-04-15
Hi guys. I am trying to dual boot my macbook 5,2 running OSX10.5 following this tutorial

[https://help.ubuntu.com/community/MacBook5-2/Karmic](https://help.ubuntu.com/community/MacBook5-2/Karmic)

and

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

Refit is up and running and I can run ubuntu 9.10 64 bit from its live CD, I've successfully installed ubuntu 9.10 but I cannot boot my new ubuntu install.

Grub 2 is working, however when I try booting kernal 2.6.31-14-generic I get the cursor & then the black screen (live CD issue with workaround mentioned in the tutorial, with the fix "acpi=off")

How can I boot my install so that I am able to upgrade the kernel?
Is there a command I can enter at the grub "edit boot"?

Thanks for the help.

---

### Post by Soupy on 2010-04-15
[SOLVED]

11) At the GRUB menu that starts after rEFIT, press E. This brings up a command list. Add acpi=off at the end of line that has your kernel version.

Looks something like this:
 /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 

12) Press ctrl+X to boot with this new parameter. 

13) Ubuntu now boots. 

Here's the thread link:

[http://ubuntuforums.org/showthread.php?t=1327758](http://ubuntuforums.org/showthread.php?t=1327758)

---

### Post by linuxopjemac on 2010-04-16
sometimes that search bar in the top right corner is helpful...

---

