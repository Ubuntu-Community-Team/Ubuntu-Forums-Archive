---
title: "Warning - Input Signal Out of Range"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by jar9357 on 2005-11-06
Hello everybody!  I am newbie to this forum and trying to install Ubuntu software to my computer. I seem to have a problem with the installation and I hope someone out there could help me out. The installation went on smoothly but after rebooting and few seconds later, my  monitor had this message "Warning - Input Signal Out of Range". My computer has an Asus motherboard, Pentium 4 1.8 GHz, 256 MB RAM and ADI Provista monitor. Please help. Thanks.

---

### Post by raublekick on 2005-11-06
I get that when I try to run FCEU and Mednafen (gaming emulators). I have no idea why it happens or how to fix it, unfortunately.

---

### Post by Maverick911 on 2005-11-06
I'm also brand new to Linux in general and ubuntu in particular, but I've been computing since before the IBM PC. I'd guess you need to tell us what brand/model video card you have before more help can be offered.

---

### Post by aysiu on 2005-11-06
It sounds as if the screen resolution Ubuntu is guessing is too high for your monitor's specifications. You can force the screen resolution to be different with some of the boot options (before you type *anything*)--press F4 or F5 to see what they are.

**Edit**: Sorry. I re-read your post. This happens *after* the installation appears to be complete? What happens when you press Control-Alt-F1?

---

### Post by jar9357 on 2005-11-07
I tried pressing Control-Alt-F1 after the error message and this appeared: 

Ubuntu 5.10 "Breezy Badger" Development Branch localhost tty1
localhost login:
Password:

I could type my user login but cannot type my password therefore I can't still login. I wonder what happened.

---

### Post by aysiu on 2005-11-07
Type in your password.
It's working. You just won't see any characters appear when you type them.
Once you're logged in, you should get something that looks like a command prompt.

At that point, type ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jar9357 on 2005-11-07
Thanks. I'll try it later.

---

### Post by jar9357 on 2005-11-07
Thanks, Aysiu! It worked! I've managed to install Ubuntu Breezy Badger 5.10 after a few tweaks with the monitor settings with the code you stated. I understand these are the basic packages and I have to be connected to the Internet to avail of the other features of Ubuntu Linux. I don't have an Internet connection at the moment but hopes to have one in the future. Right now I'll just have to content myself with exploring the possiblities of using Ubuntu Linux. Thanks again and more power!

---

