---
title: "Do I have to reinstall GRUB?"
date: 2019-08-05
forum: Apple Hardware Users
---

### Post by pteryges on 2019-08-05
Have a 2010 Mac Pro which dual boots macOS 10.13 and Ubuntu 19.04. On previous version of Ubuntu I had no problems with booting. After the 19.04 upgrade I've been having a weird boot issue.

I have efibootmgr set up to boot to the Ubuntu partition. If I restart and let it boot, I get a blank screen with a single hyphen on it which lasts for about thirty or forty seconds. Then the screen goes blank and the Ubuntu GRUB splash eventually comes up, but its only in the upper left-hand corner, like the monitor has been divided into quarters. The machine then boots into the log in screen, and everything is fine.

If I hold down the option key to get the EFI screen where I can pick which volume boots, I see the three volumes (macOS 10.13, macOS recovery volume, and the Ubuntu volume which is called something like EFI Boot.) If I pick the Ubuntu volume, I get a screen which says **System BootOrder not found. Initializing defaults.** That shows for about thirty seconds, and then I get the weird GRUB Ubuntu splash, and then it boots.

I don't think it's an EFI problem. The output of sudo efibootmgr is:

```
BootCurrent: 0000
BootOrder: 0000,0080
Boot0000* ubuntu
Boot0080* Mac OS X
Boot0081* Mac OS X
BootFFFF* 

```

I googled around and finally checked boot.log, and I see the following:

```
 Starting GRUB failed boot detection...
```

From what I've been able to find, the solution for this is to boot from the live USB and reinstall GRUB. Does that sound right?

---

### Post by gsahli on 2019-08-06
You didn't say if you've already run "update-grub."

---

### Post by pteryges on 2019-08-06
> **gsahli said:**
> You didn't say if you've already run "update-grub."

Sorry: yes, I did.

---

