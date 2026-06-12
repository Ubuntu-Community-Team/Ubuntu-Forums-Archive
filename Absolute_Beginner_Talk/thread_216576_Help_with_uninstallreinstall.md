---
title: "Help with uninstall/reinstall"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-07-15
Hi, I was wondering if I could "roll-back" to Breezy or Reinstall Dapper without
CD because I have Dapper right now..but am having some issues with the modules,
and would like to reinstall

---

### Post by zxcvbnm on 2006-07-15
Umm....Could I reinstall the  modules?...I need the hda-intel module so Ican install my sound driver.

---

### Post by molly_001 on 2006-07-15
As with most restore operations in computing, you have to put plans in place for the restore before making changes which may be undesireable.  In Breezy and Dapper, you can make an image of your linux install before any risky move, then restore it later if everything goes wrong.  You can do this now, before changes, using partImage, see here:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by catlett on 2006-07-15
I never heard of anyone going backwards but I think the principle would be the same. This would be an experiment so it is your risk to take .
To upgrade you can change your source list from breezy to dapper. So if the logic holds you should be able to replace dapper with breezy and go back to breezy.
To do this you would ```
sudo gedit /etc/apt/sources.list
```Then change all the breezy words with dapper. (gedit has a find/replace feature that makes this easy)
Then you would run ```
sudo aptitude update
``` ```
sudo aptitude dist-upgrade
``` I do not know what will happen. I think one of 2 things will happen. Either nothing will happen because apt will say the newest versions are installed or it will put all packages at the breezy level.
This is just a suggestion with nothing to support it or substantiate it. But before I did a brand new install by cd I would try it.

---

### Post by zxcvbnm on 2006-07-15
Ok thanks....but is there a way to reinstall Dapper?
I will try that if there isn't away to reinstall dapper upgrade..And report back how it goes :D

---

### Post by catlett on 2006-07-15
It will definately update to Dapper by changing the repo list from breezy to dapper.

---

### Post by zxcvbnm on 2006-07-15
Alright I think I am going to go on my linux box and try the "Expirement Method" and I'll report back/

---

