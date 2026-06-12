---
title: "NEED HELP!!! - iMac G3 Blue, Ubuntu LIVE CD Issue, Desktop doesn't load!"
date: 2007-04-08
forum: Apple PPC Users
---

### Post by cmanimevids3000 on 2007-04-08
I have an old G3 iMac Blue my sis gave me cause she didnt want it and I am trying to load ubuntu form the live cd and install it over teh mac os9 that is on it. I am trying to install version 6.10

I boot teh disk, the progress bar and then it loads and I go into Ctrl+F2 and fix the issue with the black screen in XORG.CONF and then i get the "X" cursor that turns into a regular mouse cursor and then a beige-orange background loads, and teh cd keeps making noise, and then it stops and I am still stcuk with the screen... help is appreciated XD

-CM

---

### Post by solar george on 2007-04-08
It would be best to use the alternate install cd, X is configured better during the install than on the live cd.

I would recommend that you at least try the latest [Debian]("http://www.debian.org"), it runs very fast compared to even Xubuntu on my imac G3.

---

### Post by linear on 2007-04-08
> **cmanimevids3000 said:**
> ...and then i get the "X" cursor that turns into a regular mouse cursor and then a beige-orange background loads, and teh cd keeps making noise, and then it stops and I am still stcuk with the screen... 

When you edited xorg.conf, did you [disable dri]("https://wiki.ubuntu.com/PowerPCFAQ#head-def39b758fa5328bd61aaead82e4c0588b4a4f70")?

Another possibility is the [Date Bug]("https://help.ubuntu.com/community/UbuntuDateBug").

---

### Post by anders_gud on 2007-04-09
> **cmanimevids3000 said:**
>  ...it stops and I am still stcuk with the screen... help is appreciated XD

-CM

Switch back to console and try:
killall esd

---

### Post by cmanimevids3000 on 2007-04-09
Thanks everyone, downloaded the alternate CDs for both Ubuntu and Xubuntu, Xubuntu installing no problem right now. If I don't like it I know I will love Ubuntu Cause I love GNOME! XD Thanks a bunch!

---

### Post by ZoiaGuyver on 2007-04-09
Once you get Xubuntu installed theres no reason to reinstall to have Ubuntu just open a terminal and type

sudo apt-get install ubuntu-desktop 

That will give you Ubuntu instead of Xubuntu.

---

### Post by cmanimevids3000 on 2007-04-09
There was actually an error in the Xubuntu Alt install disk so I used teh Ubuntu one I made and have had not one issue yet ^_^ (even where I had issues in the Xubuntu one)

---

### Post by ZoiaGuyver on 2007-04-09
hehe good to hear :D

Well i suppose i should say

Welcome to the world of Ubuntu PPC then :D

---

