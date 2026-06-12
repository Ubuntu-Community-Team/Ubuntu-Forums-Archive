---
title: "Wacom Tablet + Expresskeys?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Der Doktor on 2007-02-27
Hi!

I'm using a Wacom Graphire 4 Classic graphic tablet! :)
Everything works great, only the "buttons" on the tablet don't work!
I found out, that they **should** work with expresskeys, but expresskeys only sais:

> expresskeys pad
expresskeys ERROR: User named device "pad" not found!
[Here]("http://www.ubuntuusers.de/paste/7918/")'s my xorg.conf!
So what's wrong? **Can anybody help me?**

---

### Post by Tripmonkey_uk on 2007-02-28
Add this line to your “ServerLayout” section..

InputDevice “pad” 

Let me know how you get on :)

---

### Post by Der Doktor on 2007-03-03
Hi!

I added this line to my **[xorg.conf]("http://www.ubuntuusers.de/paste/8015/")**! But now, I get this error:
```
OBSERVE: xsetwacom 0.0.7 or greater was not detected on this machine
(linuxwacom-0.7.5-2 or higher is required). Since we need at least that
version for identification and other functionality, all tablets will be
treated as having no 'pad' (being 'padless'). A very limited set of
features, or none at all, will be available.

```
I found out, that my machine only has xsetwacom 0.0.**5**! :( 

**What's to do?**

---

### Post by niiiick on 2007-04-07
you have to download linuxwacom (google it, download the .tar.bz2 package) and install it;

download it to your home directory
run the following:
tar -xvf expresskeys-xxx.tar.bz2 (replace xxx with whatever package version you downloaded)
cd expresskeys-xxx
./configure
make
sudo make install


i'm at that point.  i still can't get expresskeys to work properly...let me know what you get.

---

### Post by Der Doktor on 2007-04-21
Hi!

I upgraded to Feisty Fawn in the meantime! Now, expresskeys work properly, because xsetwacom 0.1.0 is included in Feisty! :)

---

