---
title: "Bio-Linux (ubuntu framework) does not detect my windows install"
date: 2014-09-04
forum: Any Other OS
---

### Post by ryan107 on 2014-09-04
Hello,

I am trying to dual-boot ubuntu on a work computer along with Windows 7. It is a dell precision t5610, with RAID 5 set up across 3 - 2TB hard drives. However, I am having issues installing the operating system because the partition manager is not detecting the windows installation. 

In the boot menu, I am booting from "Legacy" with safe mode off. I also have the option of booting within UEFI with safe mode off. I am unsure which one would be better for what I am trying to achieve.

Should I be partitioning the hard drive within windows first?

When I run gparted after trying linux, I get a variety of errors:

"Not all of the space available to /dev/mapper/isw_cgiagccacb_ARRAY0 appears to be used, you can fix the GPT to use all of the space or continue with the current setting"
The ARRAY0 is the ~3.6TB of free space I have for use after the RAID.

I ignore this message because I'm not sure what it is asking me to do. I'm assuming this is the windows OS is what gparted is detecting? But I'm not sure what to do about it, and whether or not I should "fix" the GPT. 

Any guidance would be extremely helpful. 

-Ryan

---

### Post by grahammechanical on 2014-09-04
Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You have a UEFI boot system and if Windows 7 has been installed in EFI mode then Ubuntu must also be installed in EFI mode. You must do that to start with.

Regards.

---

### Post by QIII on 2014-09-04
Moved to Other Operating Systems and Projects

---

### Post by ryan107 on 2014-09-05
What if there is no boot option under UEFI other than "Windows boot manager" and "UEFI: Hard Drive"?

Even after going into the BIOS and adding a "CD/DVD" option, it still will not boot from the live CD. It simply returns to the BIOS screen.

Continuing to play with the BIOS settings, I cannot get the dell machine to boot from a CD while in UEFI mode. It only allows me to do it in Legacy mode, and I cannot figure out how to fix it.

---

