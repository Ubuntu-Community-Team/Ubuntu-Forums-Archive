---
title: "remove totem, install mplayer (firefox)"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by durus on 2007-01-04
I have installed mozilla-mplayer (sudo aptitude install mozilla-mplayer)
and tried to remove totem-mozilla, but can't do that.
I have also searched in the forum but can't find any thing that makes mplayer play things in firefox.

Do you know how to make mplayer the default media player in firefox and ubuntu ?

---

### Post by pissedoffdude on 2007-01-04
in your /usr/lib/firefox/plugins folder look for the totem plugins.  to remove them graphically try doing: ```
gksudo nautilus
``` if you want to remove them using the terminal try ```
sudo rm /usr/lib/firefox/plugins/*filename*
```

---

### Post by meng on 2007-01-04
On my machine, I think it's in the folder
/usr/lib/mozilla-firefox/plugins

and I just did this
cd /usr/lib/mozilla-firefox/plugins
sudo mkdir quarantine
sudo mv libtotem* quarantine/

---

### Post by rajeev1204 on 2007-01-04
LOL QUARANTINE !!!

Nice one meng . Totem deserves it .:)

---

### Post by meng on 2007-01-04
I'm glad you like it! I decided on mv rather than rm just so I could easily undo it in future.

---

### Post by durus on 2007-01-04
tanks moving the totem files worked

---

