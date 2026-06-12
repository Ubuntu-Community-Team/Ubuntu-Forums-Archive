---
title: "internet without x invironment"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by nikolaos on 2006-09-27
Does anyone know how to connect to the internet, without using gnome applications? I have BT Broadband (usb modem) and Wireless connection with a Broadcom 54g MaxPerformance 802.11. I have everything up and working under gdm invironment but i would also like to try activate them without x applications help.
Is there a guide somewhere || can anyone help?
Thanks in advance from a newbie

---

### Post by Bachstelze on 2006-09-27
Could you be more precise please ? What do you mean "activate them" ?

Oh and by the way, the desktop environment in GNOME, not GDM. GDM stands for GNOME Display Manager and it's the login screen only.

---

### Post by nikolaos on 2006-09-27
what i mean is, can i boot ubuntu without any x settings and connect to the internet.
To sudo apt-get for example

---

### Post by bodhi.zazen on 2006-09-28
Yes. You can browse, play music, edit text files, print, read E-mail, and more all without starting X.

This is why HymnToLife is asking what you want to do.

---

### Post by chrisfay on 2006-09-28
If you want to boot straight to the cli without starting GDM:

```
sudo update-rc.d -f gdm remove
```

This will stop GDM from loading at boot and will drop you at the command line instead. If you decide you want to load GDM on startup again:

```
sudo update-rc.d -f gdm defaults
```

Whether or not you load GDM, you will still have an internet connection to do whatever you need.

---

### Post by bodhi.zazen on 2006-09-29
Although this works, consdier making life easire.

```
sudo mv /mnt/hd/etc/rc2.d/S13gdm /mnt/hd/etc/rc2.d/s13gdm
```

This will disable GDM. It is easy to remember: just rename.

---

