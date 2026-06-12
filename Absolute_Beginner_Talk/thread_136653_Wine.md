---
title: "Wine?"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by chicken on 2006-02-26
Hi,
Well im trying to install wine and I get this error.
```
no suitable lex found please install 'flex' package
```

Thisis my first time using ubuntu seems great just trying to get this to work.

---

### Post by chicken on 2006-02-26
bump

---

### Post by aysiu on 2006-02-26
How are you trying to install Wine?

This way? ```
sudo apt-get install wine
```

Or some other way?

---

### Post by xhie on 2006-02-26
hwo did you install wine? with synaptic? Maybe try that if you havent.

---

### Post by chicken on 2006-02-26
I downloaded it off the winehq site and transferd it to my laptop.

---

### Post by xhie on 2006-02-26
You really are better off with synaptic or sudo apt-get install wine.

But if the laptop does not have internet access at all just make sure you have any other packages it might need.

---

### Post by chicken on 2006-02-26
Yeah it has none I need this to even try to use my internet etc, What package would i need for flex?

---

### Post by chicken on 2006-02-26
if I could skip all this and find some way to run aol 9.0 dsl on it I wouldnt need any of this :)

---

### Post by xhie on 2006-02-26
I have no idea how to get it to run AOL, since I dont use AOL, and theres alot of stuff on here about it so I guess people are having issues with it or something. 

Hehe just pack up the laptop and go sit around Panera Bread or someplace for a while, they have free internet... LOl seriously, if its just a one time thing to download updates / software you need. The time it would take to drive over there is shorter, I'm sure, then gettin AOL to work... But then again I'm really lazy..

---

### Post by chicken on 2006-02-26
:P, Id switch isp's but my parents are in love with it for some odd reason. How can I set up my wireless to work I havent figured that out either.

---

### Post by schenkin on 2006-02-26
If you are using AOL on DSL you shouldn't need the AOL client to connect to the internet. I'm pretty sure it is just an extra service you pay for in addition to your internet. What is more, I think you are paying two different companies. 

Anyway, you should be able to connect to the internet without the AOL client, as long as you aren't using AOL dialup. As for configuring wireless, that is beyond me.

---

### Post by kvorion on 2006-02-26
If running AOL is your only purpose, then you can install GAIM instant messenger, which supports multiple protocols including AOL, yahoo, MSN, jabber and the like.

---

### Post by GQed76 on 2006-03-04
yet noone can say how he can get flex.  He wants the latest version of wine that isnt 8 months old.  Flex is a required package...

I found flex in synaptic.  Also you will need bison..hope this helps

---

### Post by pbransford on 2006-03-04
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

Also, make sure you have universe and multiverse repositories enabled. You can do this straight from the synaptic package manager. Installing wine from apt, aptitude, synaptic (or any other APT system) will then automatically try to grab flex (i have only the universe, multiverse, backports, and wine.hq repos enabled, no issues here)

BTW, being new to wine, you may be interested in this: [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)
> WineTools - WineTools is a menu driven installer for installing Windows programs. This software lets you install the following Windows software: DCOM98, IE6, Windows Core Fonts, Windows System Software, Office & Office Viewer, Adobe Photoshop 7, Illustrator 9 and many other programs.
By Joachim von Thadden.

---

