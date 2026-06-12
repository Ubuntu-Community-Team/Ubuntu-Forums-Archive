---
title: "Help- Gnome problem!"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by tbasherizer on 2007-02-16
Today I logged onto my computer as my default user, in gnome. I noticed the screen resolution was too small, so I went into xserver reconfiguration, and mucked around. I tried to log in on gnome, and it only showed that cursor that flashes in the upper left hand corner of the screen. I typed reboot the first time, and now, when I log into gnome, I only see my "reboot" and that cursor right below it. I'm in KDE right now, so this isn't an emergency, but I really don't like the format of KDE. I didn't like it in slackware, and I don't like it here. Could someone tell me how I can remedy my problem?

---

### Post by Sklasko on 2007-02-16
Try typing "sudo dpkg-reconfigure xserver-xorg" and going from there, then try logging back into Gnome.

---

### Post by meng on 2007-02-16
Or more accurately
sudo dpkg-reconfigure xserver-xorg

---

### Post by Sklasko on 2007-02-16
:o Sorry, didn't notice that.

---

### Post by tbasherizer on 2007-02-18
I did that before, but it didn't work. I also re-installed every GNOME package to be heard of, but it still didn't work.

---

