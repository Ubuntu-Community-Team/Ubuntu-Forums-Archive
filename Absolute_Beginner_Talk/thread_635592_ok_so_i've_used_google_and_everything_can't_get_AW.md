---
title: "ok so i've used google and everything can't get AWN"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2007-12-08
is there anyway i can just like download it or something? or does someone have a terminal code that they know works?

---

### Post by Flying caveman on 2007-12-08
[http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon](http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon)  first thing that came up when i googled ubuntu AWN,  I don't even know what it is ):P

---

### Post by Matt Yun on 2007-12-08
Ironically enough, this thread appeared right next to [HOW-To: Awn curves]("http://ubuntuforums.org/showthread.php?t=572019").  When you google, it's more effective if you search with "ubuntu" and/or "gutsy" in your keywords.

For the default AWN theme, add the following to /etc/apt/sources.list:

```
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

```
Then download the gpg-key for the awn repository:

```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
sudo apt-get update
```

And finally, to install awn:

```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

---

### Post by daimaru on 2007-12-08
you can also go to [http://getdeb.net]("http://getdeb.org/") search for awn there and download the .deb file. but i like the repository stuff posted above me better ;)

---

