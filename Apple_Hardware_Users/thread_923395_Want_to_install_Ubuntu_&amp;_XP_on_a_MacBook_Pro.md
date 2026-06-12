---
title: "Want to install Ubuntu &amp; XP on a MacBook Pro"
date: 2008-09-18
forum: Apple Hardware Users
---

### Post by bgreenaway on 2008-09-18
Hi Everyone

I have a MacBook Pro Intel Core 2 Duo 2.33 Ghz 2 GB RAM 160 GB SATA currently running Mac OS X 10.4.11. Although I love the hardware, I am not too keen on the Mac OS, so have decided to scrub the Mac OS and install Ubuntu 8.04 from scratch (or Kubuntu, which I am leaning toward). I want to have a 120 GB partition for Ubuntu and the remaining 40 GB spare for Windows XP because I want to run some legacy apps for work. I want to have the option to dual boot using rEFit.

Given that Boot Camp is no longer available for Tiger and I have no intention of buying a Leopard upgrade, can I just go ahead and boot and install from the Ubuntu (or Kubuntu) Live CD and partition the disk accordingly? Also, what format should the second partition be for Windows XP?

Any idiot-proof help gratefully received :confused:!!

---

### Post by cyberdork33 on 2008-09-18
> **bgreenaway said:**
> Hi Everyone

I have a MacBook Pro Intel Core 2 Duo 2.33 Ghz 2 GB RAM 160 GB SATA currently running Mac OS X 10.4.11. Although I love the hardware, I am not too keen on the Mac OS, so have decided to scrub the Mac OS and install Ubuntu 8.04 from scratch (or Kubuntu, which I am leaning toward). I want to have a 120 GB partition for Ubuntu and the remaining 40 GB spare for Windows XP because I want to run some legacy apps for work. I want to have the option to dual boot using rEFit.

Given that Boot Camp is no longer available for Tiger and I have no intention of buying a Leopard upgrade, can I just go ahead and boot and install from the Ubuntu (or Kubuntu) Live CD and partition the disk accordingly? Also, what format should the second partition be for Windows XP?

Any idiot-proof help gratefully received :confused:!!

For your situation, I think you should just convert the disk to a normal MBR (non-GPT) partition format and partition just like you would on a PC. Installing Ubuntu. rEFIt is probably not a good choice unless you keep OS X. GRUB will work fine to boot between Ubuntu and Windows.

Format the windows partition however you want to, NTFS or FAT32 are really your only options. Note that if you install Windows after Ubuntu is installed, it will likely wipe out grub and you will have to reinstall it again to get back in to Ubuntu.

---

### Post by bgreenaway on 2008-09-18
Thanks for the reply Cyberdork33. 

I've been thinking and what I will probably do is rather than mess around with multiple partitions and dual boot options, I will just partition the entire disk for Ubuntu and install VirtualBox, which I have used before and run XP in the virtual machine. I can then run Ubuntu and XP concurrently.

Your thoughts?

---

### Post by cyberdork33 on 2008-09-18
> **bgreenaway said:**
> Thanks for the reply Cyberdork33. 

I've been thinking and what I will probably do is rather than mess around with multiple partitions and dual boot options, I will just partition the entire disk for Ubuntu and install VirtualBox, which I have used before and run XP in the virtual machine. I can then run Ubuntu and XP concurrently.

Your thoughts?
that is a valid option if you are willing to deal with a non-native install of Windows (which can be ok).

Good Luck

---

### Post by bgreenaway on 2008-09-18
OK, if I decide to go with XP on one partition and Ubuntu on the other, should I install XP first to avoid GRUB from being wiped out as per your earlier post?

---

### Post by mercenaryhmster on 2008-09-18
that would be the best way to do it

---

### Post by cyberdork33 on 2008-09-18
> **mercenaryhmster said:**
> that would be the best way to do it
yep, I would just create all your partitions before installing anything.

---

