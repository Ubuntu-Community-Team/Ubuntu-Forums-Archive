---
title: "where is the &quot;boot.ini&quot; of ubuntu"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by xeth on 2007-10-14
I'm looking for the boot.ini like of windows in ubuntu as I've been constantly updating gutsy gibbon. The list of the boot is getting longer with the different versions of the kernel and I like to clean it up. 

Also does ubuntu have  utilities that can clean up junk like unused dependencies, or other kinds of junk. I've noticed that when I upgrade to gutsy gibbon many packages were obsolete.

---

### Post by LowSky on 2007-10-14
go into synaptic and deleted the old linux kernals and keep the two newest ones and it will clear out you grub files... or as you like to call it by Windows terms boot.ini


also use ```
 sudo apt-get clean
```

---

### Post by AnRa on 2007-10-14
> **xeth said:**
> I'm looking for the boot.ini like of windows in ubuntu as I've been constantly updating gutsy gibbon. The list of the boot is getting longer with the different versions of the kernel and I like to clean it up.
/boot/grub/menu.lst

> **xeth said:**
> Also does ubuntu have  utilities that can clean up junk like unused dependencies, or other kinds of junk. I've noticed that when I upgrade to gutsy gibbon many packages were obsolete.
sudo apt-get autoremove
sudo apt-get autoclean

---

