---
title: "Official Mozilla Firefox 2.0.0.3 install"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by nvteighen on 2007-05-28
Hi, I've been trying to download and install the official Firefox build, but I get stuck after extracting the tarball... Where should everything go? I've tried using the help on MozillaZine ([http://kb.mozillazine.org/Installing_Firefox#Linux](http://kb.mozillazine.org/Installing_Firefox#Linux)), but I don't get it starting.

I know there is the Ubuntuzilla script and also tried it, but does it actually install an official build?

Ah, every install attempt I've done has been after a complete removal of previous Firefoxes (including Ubuntu's build)

Thanks!

---

### Post by meborc on 2007-05-28
if you compile stuff from source be sure to install build-essential package first, it contains all you need to install from source...

you probably got some error when ./configure inside the folder... what was it? you might be missing a dependency

---

### Post by Kobalt on 2007-05-28
Ubuntuzilla installs an official build of the latest Firefox, you should use it...

---

### Post by nvteighen on 2007-05-28
@ meborc: I didn't even try to "./configure"! I wanted to extract everything into /usr/local (see [this link]("http://kb.mozillazine.org/Installing_Firefox#Linux")), but soonly realized Ubuntu's firefoz wasn't there so I were wrong... I tried to put into /usr/lib/ (where Ubuntu Firefox is installed), changed ownership of everything to root (sudo chown -R root:root...), but then it didn't work. I think there's no need to compile here... or is there?

@ Kebolt: If I can get it work from Mozilla, I'll use the script. (I want to learn a bit... that's why I'll use the tarball first)

---

### Post by sultanoswing on 2007-05-28
[http://www.getswiftfox.com/](http://www.getswiftfox.com/)

...faster / better / stronger

...and now there's an Ubuntu Repo:

[http://getswiftfox.com/builds/debian/branch](http://getswiftfox.com/builds/debian/branch)

---

