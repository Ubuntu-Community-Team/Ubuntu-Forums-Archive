---
title: "help changing vga problem"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by andekhi on 2007-05-13
i have change my vga from ati to nvidia, and when i start ubuntu, it's said that X server is disable and i know exactly why. my question in redhat there is kudzu and system-config-display, i don't know tools to fix it in ubuntu. can some one help me??

thx in advance


andekhi

---

### Post by taurus on 2007-05-13
You cannot use nvidia in /etc/X11/xorg.conf until you have installed nVidia driver for your graphic card.  Therefore, you need to edit /etc/X11/xorg.conf

```
sudo nano -Bw /etc/X11/xorg.conf
```
and replace the "nvidia" with "nv" as the Driver for your graphic card.  Save it with <Ctr>o and exit with <Ctrl>x.  

Now, see if X is running again.

```
sudo /etc/init.d/gdm start
```

---

### Post by andekhi on 2007-05-13
thx sir it works.. :D

---

