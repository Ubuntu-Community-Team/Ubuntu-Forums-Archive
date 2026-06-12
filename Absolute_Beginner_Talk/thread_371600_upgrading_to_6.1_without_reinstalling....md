---
title: "upgrading to 6.1 without reinstalling..."
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-02-27
so, how do i upgrade my ubuntu 5.10 to 6.1 or whatever the newer version is without reinstalling? thanx in advance.

---

### Post by Anicka on 2007-02-27
sudo aptitude update && sudo aptitude upgrade
gksudo "update-manager -c"

You will have to do the update-manager thing once for every step on the upgrade-ladder. 6.10 is the last stable verion.

Fix any problems you might get with a new version before upgrading further.

Good luck!

(This is the official version, unofficially you could change you source-list so that all it says Edgy instead of Breezy and run aptitude, but that is more likely to be troublesome)

---

### Post by TonKi on 2007-02-27
[https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades")

It can be helpful to install ubuntu-desktop again, to avoid trouble

---

### Post by TonKi on 2007-02-27
> **Anicka said:**
> 
gksudo "update-manager -c -d"


*-d, --devel-release   Check if upgrading to the latest devel release is possible*
not what he wants ;)

---

### Post by STREETURCHINE on 2007-02-27
yes you can only upgrade from dapper to edgy,breezy is a bit to far down the line

---

### Post by Anicka on 2007-02-27
Sorry, cut and paste to quickly... I didn't dubble check it and I should since I didn't recognise the -d.

Conclusion: don't trust info from wikis...

gksudo "update-manager -c"
is the one to use.

---

### Post by the_nomad on 2007-02-27
first of all thank you all for replying me.

i have just made that (sudo aptitude upgrade/upgrade)... so now i have the latest version of ubuntu? 6.10?

---

### Post by MickS on 2007-02-27
I have just tried to upgrade my system that way and the process came to a grinding halt and threw up this message:-  Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz) 301 Moved Permanently

Any ideas what I can do about it, I am suspicious that I have to remove something first?

TIA

Mick

---

### Post by TonKi on 2007-02-27
Seems like you have an entry in your sources.list that doesn't exist anymore.
Edit your sources.list.
```
sudo nano /etc/apt/sources.list
```
find the line you posted and comment it (put a # in front) or delete it.

---

### Post by MickS on 2007-02-27
I shall try that when I have time, thanks for your quick response, as an aside can you tell me roughly how long the process takes.

Mick

---

### Post by rabid9797 on 2007-02-27
depends what build of what version your coming from, and how fast your cpu and internet is.

for me, coming from the final dapper to edgy final took me about 45 minutes downloading and getting everything installed.

---

