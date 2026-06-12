---
title: "modprobe.d broke xserver"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2007-03-27
I ran the following command which I used in dapper to fix a sound problem with ich6 in Feisty ( sudo modprobe snd_intel8x0 ac97_quirk=hp_mute_led). Now my Xserver is broken. It will start, but wont display properly. ie... no gnome panel or anything else useful. It just displays my wallpaper. 

Does anyone know how to undo this modprobe command? sudo modprobe snd_intel8x0 ac97_quirk=hp_mute_led

---

### Post by bulldog on 2007-03-27
Maybe just```
sudo dpkg-reconfigure xserver-xorg
``` but I really don't know.

---

### Post by DSn0wMan on 2007-03-27
Believe me that was the first thing I tried. No Dice!

---

### Post by Falados on 2007-03-27
Try ```
rmmod snd_intel8x0
```

If that doesn't work, then put

blacklist snd_intel8x0

in your /etc/modprobe.d/blacklist file

I don't know how a sound module would prevent gnome from loading though... its strange.

---

### Post by DSn0wMan on 2007-03-27
It must have been something else that got updated before I restarted. I am guessing it was a compiz update since I have a compiz entry in /var/crash. I will try disabling compiz / desktop effects.

---

