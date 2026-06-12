---
title: "Installing Updates"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by avanrens on 2007-04-21
After installing the 353 updates 7.04 won,t boot. I reinstalled the beta version, but want to know which selected updates to install so 7.40 will work or should I just stay with the beta version as at least it works.

---

### Post by forrestcupp on 2007-04-21
If you're using a proprietary video driver, it may have updated the kernel without updating the linux-restricted-modules.  This happened to me.  Try rebooting, and when grub starts, hit escape to go into the menu.  Choose a previous version of the kernel, and it should boot.  You'll have to do this until you can update the restricted modules to the latest kernel version.

---

