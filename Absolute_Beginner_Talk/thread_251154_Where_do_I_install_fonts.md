---
title: "Where do I install fonts?"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by wsun on 2006-09-05
Hi, I'm wondering where to put a chinese font that I dled? How do I install it? Thanks

---

### Post by MaximB on 2006-09-05
system>preferences>fonts>details>go to font folder>extract them here !

---

### Post by wsun on 2006-09-05
it doesnt seem to work, I extract it but the file does not end up in that folder. All the fonts have a little lock icon on them also..

---

### Post by GeneralCody on 2006-09-05
I would say the easiest way of getting and installing fonts, is using easyubuntu.

It does a lot more as well, like adding capability to play DVD's, update your package repositories, and a lot more!

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Note: Some of theese components may be issue to copyright infrigements
(check the rules for your country ;-)

GeneralCody

---

### Post by GeneralCody on 2006-09-05
Oh... I didn't see thet chineese part... Try doing a fc-cache ind a terminal, after extracting your fonts.
Allso make sure that yor fontdir is referenced in your xorg.conf file...

GC

---

### Post by GeneralCody on 2006-09-05
> **GeneralCody said:**
> Oh... I didn't see thet chineese part... Try doing a fc-cache ind a terminal, after extracting your fonts.
Allso make sure that yor fontdir is referenced in your xorg.conf file...

GC

Looks like you have done this as root, with sudo. Try allso making the files read/writable by world:

sudo chmod -r a+rw /path/to/the/fonts/*
This removes the "padlock". (you actually only need read access to fonts, so -r instead of -rw would suffice.

You could allso make a personal font directory, ex. mkdir /home/yourname/fonts, and extract to there, and include that path in your /etc/X11/xorg.conf file...

GC

---

### Post by urukrama on 2006-09-05
Go the folder /home/USERNAME/.fonts/ and just copy your fonts into that folder. (It is a hidden folder, so either type out the location, or enable 'view hidden files'). 

If you do it in this way, only when you are logged in as USERNAME will the fonts work. If you want for all usernames, you'll have to log in as root to copy the fonts to the folder mentioned in an earlier post.

It took me also a while before I got this... :)

---

### Post by sunny_nwho on 2006-09-09
just did wht u said did not work :( and by the way will *.otf files also work in the same way as *.ttf

---

