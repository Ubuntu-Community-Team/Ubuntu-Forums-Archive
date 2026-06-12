---
title: "Not play any audio, video"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2006-12-07
hi guys i am using mplayer, rhythambox music player but nothing is play any audio video format.
:( :( :(

---

### Post by taurus on 2006-12-07
You need to install the codecs first.  You can use automatix2 to do that...

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by igknighted on 2006-12-07
Read the sticky at the top of the page, mp3's and other a/v formats are not free and therefor are not included in Ubuntu by default.

EDIT: Beat me to it, sorry, they removed the sticky I was refering to.  Automatix2 is your best bet

---

### Post by lucky_chouhan on 2006-12-07
Hi taurus  i am try your steps. but i am get this -

FATAL ERROR - Media Players
An apt-based error occured  and installation was unsccuessful.


what i do:( :(

---

### Post by taurus on 2006-12-07
Can you paste your /etc/apt/sources.list here?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by S1NGH on 2006-12-07
umm...do you have the following in your sources.list file:

```
## Automatix repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
```

---

### Post by lucky_chouhan on 2006-12-07
yes i am already downloaded automatix 2.

---

### Post by taurus on 2006-12-07
And did you use it to install the codecs for your machine?

---

### Post by lucky_chouhan on 2006-12-08
YES I TRYING TO INSTALL CODECS BUT I FOUND THIS.

FATAL ERROR - Media Players
An apt-based error occured and installation was unsccuessful.

---

