---
title: "pidgin install"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by liniaal on 2007-08-08
hello,

i recently tried to install pidgin from source with the following commands
./configure
make
sudo make install

without modifying anything.. but when i try to launch it i get a screen with no readable characters, like this:
[IMG]http://wie-is-je-vader.herejezus.nl/img/wtf.png[/IMG]
[SIZE="1"](sorry for the xxlarge image.)[/SIZE]

also the terminal from which i launched, will display tons of "pango"/"cairo" errors.
what have i done wrong?! no extreme errors came out of configure.sh, i think.
btw. i use ubuntu 6.10 desktop.

---

### Post by AndyCooll on 2007-08-08
It might be worth you uninstalling that lot and installing the version on [GetDeb.net]("http://www.getdeb.net/release.php?id=1209")

Since I had the earlier version installed it threw up a few errors initially, so I uninstalled the previous version. The install then went smoothly and the app works fine too. AP

---

### Post by Hospadar on 2007-08-08
you are probably missing some dependancies (the fonts) that might not show up in the configure script for whatever reason.  I would uninstall at and look for the .deb, or try and figure out which font it uses and install that.

Also I'd just use gaim, it's the same software, but they had to rename it for legal reasons.  The gaim in the repos mushes really well into gnome.

---

### Post by Arwen on 2007-08-08
I tried to uninstall Gaim through Applications->Add/Remove and it couldn't do it cause other applications depend on it and that I could remove it by synaptic.In synaptic I found that I had installed gaim and gaim-data and all the other packages where unticked.Should I just untick the 2 packages or is there anything else I should remove?

---

