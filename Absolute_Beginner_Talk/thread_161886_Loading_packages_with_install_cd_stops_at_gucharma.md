---
title: "Loading packages with install cd stops at gucharmap"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Mykewl on 2006-04-17
Installing from Install cd works fine until packages load after the reboot.
It always stops at gucharmap. I choose to erase the hard drive and partion.
Today I tried to erase and use the LVN (?) and it installed. Now I have edubuntu instead of Ubuntu.
Any suggestions ](*,) 
Thanks

---

### Post by Qrk on 2006-04-18
Make sure you don't have you install cd in you drive, and then open up a terminal and type:

```
sudo apt-get install ubuntu-desktop
```

This will install the packages that you are missing from Ubuntu, but will not uninstall edubuntu.

---

