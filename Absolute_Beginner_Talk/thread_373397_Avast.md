---
title: "Avast"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-03-01
Ok all, still being new to ubuntu and I do mean new, I installed the linux.deb package of Avast to my system. I have good luck with home version for windows for  a very long time. It installed and does not show up in menu at all. How do I get this thing to launch?

---

### Post by Mizled on 2007-03-01
```
sudo avastgui
```


This command works for me. :) Goodluck


Edit: You will have to make a Launcher and add to be able to click it. You shouldn't get viruses on your Linux box but when I think somethings fishy with my *nix box I just use the command above. Hope this helps.

---

### Post by J11Gyro on 2007-03-01
Thanks, I kinda got it working but not with terminal, used the menu editor and set it up. I do like the terminal though, much easier.

---

### Post by Mizled on 2007-03-01
You can also run the command...

```
sudo avast
```

If you don't like the gui version.

---

### Post by maniacmusician on 2007-03-01
For future reference, when opening graphical apps with sudo, you should use "gksudo" (if you're using GNOME) or "kdesu" (if you're using KDE) instead of sudo.

---

### Post by makan on 2007-04-18
run this command:

sudo /usr/lib/avast4workstation/share/avast/desktop/install-desktop-entries.sh install

avast will appear under "Application -> Accessories" menu

---

### Post by girard on 2007-08-21
> **makan said:**
> run this command:

sudo /usr/lib/avast4workstation/share/avast/desktop/install-desktop-entries.sh install

avast will appear under "Application -> Accessories" menu

i get this when running that:

> 
$ sudo /usr/lib/avast4workstation/share/avast/desktop/ins tall-desktop-entries.sh install
sudo: /usr/lib/avast4workstation/share/avast/desktop/ins: command not found


i know i can create a custom launcher, but i'd like to figure out why it doesn't show up in the menu. my previous installation, worked well. i wonder what went wrong with this one. could something happened in my clean install of edgy and online upgrade to fiesty?

---

### Post by bme on 2007-08-21
just for curiosity,why do you want an antivirus on ubuntu? isn't it secure enough against viruses?

---

### Post by Dark Star on 2007-08-21
> **maniacmusician said:**
> For future reference, when opening graphical apps with sudo, you should use "gksudo" (if you're using GNOME) or "kdesu" (if you're using KDE) instead of sudo.

2nd that :) Avast is good.. But Av in Linux :lolflag:

---

### Post by AceofSpades19 on 2007-08-21
there is no need to install Avast on Ubuntu

---

### Post by bloozman on 2007-09-09
> **girard said:**
> i get this when running that:



i know i can create a custom launcher, but i'd like to figure out why it doesn't show up in the menu. my previous installation, worked well. i wonder what went wrong with this one. could something happened in my clean install of edgy and online upgrade to fiesty?

makan inadvertantly included a space in the original command he provided.
run this and it will work fine for you:
sudo /usr/lib/avast4workstation/share/avast/desktop/install-desktop-entries.sh install

edit: I see why the error occured .... when I paste the command into the reply, the forum editor inserts a space in the word "install" so that it looks like this: "ins tall-desktop-entries.sh" ..... just remove the space in a text editor so the last part of the command looks like this: "/install-desktop-entries.sh install"

---

