---
title: "Package reverting"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Ateo on 2007-05-05
After an update yesterday of 4 packages, one of them broke GAIM (on my install). My question is, in order to verify that it was an update (which it most likely was since I didn't install anything between the update yesterday and my reboot this morning)...

Basically, I need to revert the following, if it's even possible:

app-install-data (0.3.30) to 0.3.31
gnome-app-install (0.3.30) to 0.3.31
python (2.5.1-0ubuntu2) to 2.5.1-0ubuntu3
python-minimal (2.5.1-0ubuntu2) to 2.5.1-0ubuntu3

How can this be done?

Thanks

---

### Post by mikeyphi on 2007-05-05
Have a look for the old packages under /var/cache/apt/archives
If there are there you could use synaptic to remove the latest files and install the old ones by double clicking on each of them.
If anything goes wrong you can still reinstall the latest files.

You might want to consider using 'simple back up' so that you can revert if you have a problem in future?

---

### Post by starcraft.man on 2007-05-05
> **Ateo said:**
> After an update yesterday of 4 packages, one of them broke GAIM (on my install). My question is, in order to verify that it was an update (which it most likely was since I didn't install anything between the update yesterday and my reboot this morning)...

Basically, I need to revert the following, if it's even possible:

app-install-data (0.3.30) to 0.3.31
gnome-app-install (0.3.30) to 0.3.31
python (2.5.1-0ubuntu2) to 2.5.1-0ubuntu3
python-minimal (2.5.1-0ubuntu2) to 2.5.1-0ubuntu3

How can this be done?

Thanks

Easy enough, but you may just want to install pidgin instead after removing gaim, gaim is being discontinued in favor of pidgin i think >.>

Open terminal, and type in:

```
sudo aptitude remove gaim
```

Then use the debian on this page, should work fine :)

If you do want to downgrade though, you can do taht too.

Step 1, open package manager... System > Administration > Synaptic pakcage manager.

Step 2, Search for what you want to downgrade, search button is on the right. You want to put in the four files you listed seperately.

Step 3, select the file, right click and choose properties. Click the versions tab, select the old version and then you can force it to downgrade.

Step 4, repeat for others. Then if you want to prevent notifier from telling you to update, select them all and go to Package > Lock Version.

Thats it.

---

### Post by Ateo on 2007-05-05
Yea. I decided screw GAIM.. hehe.. I found a pidgin 2.0.0 deb package, installed it. works like a charm...

For those wanting a debian package, here is what I used:

[http://gnome-look.org/content/show.php/Pidgin+2+DEB?content=57356](http://gnome-look.org/content/show.php/Pidgin+2+DEB?content=57356)

---

### Post by starcraft.man on 2007-05-05
Have fun with Pidgin then, remember to feed them bread crumbs or they will peck your brains out :p

---

