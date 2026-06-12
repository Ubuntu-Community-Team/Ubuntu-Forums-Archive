---
title: "[SOLVED] quick question about X"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Kymus on 2007-11-27
alright, I'm about to fiddle with trying to enable the [ATI big desktop]("http://ubuntuforums.org/showthread.php?t=301941") but I am paranoid that something will go wacky and X will get 3-kinds of messed up because that's my luck. So I've got 2 questions:

[LIST=1]
[*]how would I replace the backup copy of X with the current, if need be?
[*]there's a way to restore X to default settings, isn't there? (I thought I had this written down once upon a time)
[/LIST]

---

### Post by PriceChild on 2007-11-27
```
sudo dpkg-reconfigure xserver-xorg -pcritical
```will restore your xorg.conf to the default settings.

---

### Post by Kymus on 2007-11-27
thank you PriceChild!

now how can I go about replacing the current X file with the backup file of X?

---

### Post by benrboone on 2007-11-27
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

this will copy the current xorg.conf to backup

sudo cp /etc/X11/xorg.backup /etc/X11/xorg.conf.conf

this will replace your existing xorg.conf with the backup one (if you created it with the name xorg.backup)

---

### Post by Kymus on 2007-11-27
> **benrboone said:**
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

this will copy the current xorg.conf to backup

sudo cp /etc/X11/xorg.backup /etc/X11/xorg.conf.conf

this will replace your existing xorg.conf with the backup one (if you created it with the name xorg.backup)

thanks!

---

