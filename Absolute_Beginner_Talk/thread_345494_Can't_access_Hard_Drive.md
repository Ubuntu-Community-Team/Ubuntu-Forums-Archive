---
title: "Can't access Hard Drive"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by weagle07 on 2007-01-24
I've been using Ubuntu 6.06 x86 64-bit for about 3 months and just recently did a format reinstall to the 32-bit version because of the availability of some software that I needed.  I installed all 214 updates that were available and  installed the build-essential files as i did for the 64-bit version.  I don't think any of these actions are what's causing my problem.  My problem I think is in the grub menu.lst file.  I commented out the memory test, etc. and left just the main ubuntu kernel and Windows XP Pro as the only boot options.  I then restarted my computer and after about what seemed like a 20 second hang coming out of the bios i got a Grub loader error 16.  I then went into the bios and it does see the hard drive which ubuntu is installed on, but I'm not able to access it.  I tried using the live cd to navigate back to the menu.lst file to correct it, no go.  I tried to reinstall ubuntu on the drive, but the install freezes and says it can't recognize hardware configuration.  I also tried to use partition magic from windows, which sees the drive, but when I try to format the drive I get errors.  I'm lost at what else to do.. any suggestions? :confused:

---

### Post by tagginannie on 2007-01-24
> **weagle07 said:**
> I've been using Ubuntu 6.06 x86 64-bit for about 3 months and just recently did a format reinstall to the 32-bit version because of the availability of some software that I needed.  I installed all 214 updates that were available and  installed the build-essential files as i did for the 64-bit version.  I don't think any of these actions are what's causing my problem.  My problem I think is in the grub menu.lst file.  I commented out the memory test, etc. and left just the main ubuntu kernel and Windows XP Pro as the only boot options.  I then restarted my computer and after about what seemed like a 20 second hang coming out of the bios i got a Grub loader error 16.  I then went into the bios and it does see the hard drive which ubuntu is installed on, but I'm not able to access it.  I tried using the live cd to navigate back to the menu.lst file to correct it, no go.  I tried to reinstall ubuntu on the drive, but the install freezes and says it can't recognize hardware configuration.  I also tried to use partition magic from windows, which sees the drive, but when I try to format the drive I get errors.  I'm lost at what else to do.. any suggestions? :confused:


It means the MBR is messed up If you can boot Windows or use a recovery
boot disk and press "R" to get in to Recovery Console and type "FixMBR" and 
run "CHKDSK"  Now try to reinstall Ubuntu.

Suzy:KS

---

