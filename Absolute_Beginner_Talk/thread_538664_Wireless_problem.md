---
title: "Wireless problem"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by loyaleagle on 2007-08-30
Hello everyone;

I am able to connect to my wireless network using manual configuration settings, however when using roaming it does not work. I use a 128 HEX key. I tries both the open and shared key. (Shared locks my system and I have to reboot). 
This is not so much a problem at home. I use the manual config and all is well. However, when I leave home and want to use my wireless with roaming, then I am out of luck.

Any ideas?

Thanks for all the help.

Loyaleagle:KS

---

### Post by sstucke on 2007-08-30
Please tell us the following:
Which version of ubuntu are you using?
Which encryption system do you use? (WPA or WEP)
Do you hide your SSID from broadcasting?

Sebastian
[http://en.tuxero.com]("http://en.tuxero.com")

---

### Post by loyaleagle on 2007-08-30
I am using Feisty
Encryption is WEP
SSID is broadcasting

Thanks

---

### Post by sstucke on 2007-08-30
Ok, you shouldn't need to set your configuration to manual.
Just let gnome applet detect the wifi network, and connect to it. It will prompt you to create a keyring, so next time it will fetch the wep password from the keyring.
Hope this helps.

---

