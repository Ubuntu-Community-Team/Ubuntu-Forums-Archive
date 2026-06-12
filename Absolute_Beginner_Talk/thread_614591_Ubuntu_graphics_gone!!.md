---
title: "Ubuntu graphics gone!!"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Morphed1 on 2007-11-16
Hi folks. I installed Ubuntu with great sucsess about a month ago. Yesterday I hooked my laptop to my lcd  tv. Everything worked fine, until I rebooted the machine.

The ubuntu loader is clear as always, but when I am supposed to come to the loginscreen, the graphics are just really screwed. Impossible to see anything. This goes for my laptop screen and i cant even find my  lcd tv anymore even though the sound can be heard from the tv via audio-cabel.

So basically, I cant see anything at all. Please give me a helping hand!!!

Thanks

---

### Post by overdrank on 2007-11-16
> **Morphed1 said:**
> Hi folks. I installed Ubuntu with great sucsess about a month ago. Yesterday I hooked my laptop to my lcd  tv. Everything worked fine, until I rebooted the machine.

The ubuntu loader is clear as always, but when I am supposed to come to the loginscreen, the graphics are just really screwed. Impossible to see anything. This goes for my laptop screen and i cant even find my  lcd tv anymore even though the sound can be heard from the tv via audio-cabel.

So basically, I cant see anything at all. Please give me a helping hand!!!

Thanks

HI and welcome, when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by hyper_ch on 2007-11-16
reboot is not needed.... just x-server restart. You can do that with CTRL+ALT+BACKSPACE

---

