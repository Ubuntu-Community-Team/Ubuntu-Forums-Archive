---
title: "UNR interface on a PPC Mac?"
date: 2010-04-05
forum: Apple Hardware Users
---

### Post by jfmanamtr on 2010-04-05
I have been searching for this, but can't seem to find a definite answer. I am running Ubuntu 9.10 on my iBook G3. The gnome interface seems to be a little much for it. I am trying to find out if there is anyway to put UNR on an iBook G3 or at least the stripped down interface. Can this be done?
 
~John

---

### Post by linuxopjemac on 2010-04-05
I have no idea about Ubuntu Netbook Remix, but I can advize LXDE. It rocks on your iBook G3. I have it on a G3 PowerBook 400 MHz.

```
sudo apt-get install lxde-desktop
```

Next time you login, you choose as session LXDE. You will like it.

---

### Post by jfmanamtr on 2010-04-05
Ok. Can I then remove Gnome all together & how can I do that?
 
~John

---

### Post by linuxopjemac on 2010-04-05
first try if you like it ;)

---

### Post by jfmanamtr on 2010-04-05
Fair enough. I will try it out once I get home. I could do it remotely, but I am at work & we have no bandwidth.
 
~John

---

### Post by jfmanamtr on 2010-04-05
Ok. I tried using that apt-get & it didn't work. So, I did sudo apt-get install lubuntu-desktop. That worked. I am having issues making LXDE play nice with my wireless. I have it setup for WEP (I have a few older laptops that won't do WPA). I enter the key & WCID tells me that it never receives an IP address. It also messed up gnome's network manager. So, I am writing to you from a desktop now. Any ideas?
 
~John

---

### Post by linuxopjemac on 2010-04-06
I had an issue like that as well.

[http://forums.debian.net/viewtopic.php?f=5&t=50462](http://forums.debian.net/viewtopic.php?f=5&t=50462)

---

### Post by jfmanamtr on 2010-04-06
Weird thing is that it seems to have completely removed network-manager & network-manager-gnome. I got to get all that turned back on first. Whoops!
 
~John

---

### Post by linuxopjemac on 2010-04-06
I didn't have that under Debian....You might want to start nm-applet.
```
nm-applet
```

[http://wiki.lxde.org/en/LXSession](http://wiki.lxde.org/en/LXSession)

---

### Post by psko on 2010-05-19
I am going to try to get UNR working on my PPC PowerBook. Here's a similar thread: [Will Ubuntu 10.04 netbook remix run on a mac mini ppc g4? ]("http://ubuntuforums.org/showthread.php?t=1474827").

---

