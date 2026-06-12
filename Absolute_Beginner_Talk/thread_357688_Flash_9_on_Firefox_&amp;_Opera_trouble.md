---
title: "Flash 9 on Firefox &amp; Opera trouble"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by mekkah on 2007-02-09
I'm kinda having trouble displaying flash correctly. i've downloaded the latest version & followed the instructions, but it only seems able to install it for firefox (Opera is my main browser) and not very good either. My girlfriend is a big youtube enthusiast & gets pissed of because the videos won't display properly.

I've even tried to make an manual install, but nothing seems to work. Any clues someone :confused:

---

### Post by RomeReactor on 2007-02-09
Hi. First, close opera. Then, from the file you downloaded at Adobe's site, extract the **libflashplayer.so**; now open a terminal and type

```
sudo nautilus
```

copy *that* libflashplayer.so and press **CTRL+H**; then go to **/home/USER_NAME/.opera/plugins**, delete the old libflashplayer.so and paste the new one there. Open Opera and go to YouTube and see if the videos work properly now.

---

### Post by hanexar on 2007-02-09
I install mine directly with automatix

[http://getautomatix.com/](http://getautomatix.com/)

It saved me lots of problems, maybe it is the easy solution...

---

### Post by mekkah on 2007-02-10
Now it works with firefox, but opera keeps looking like this:
[[IMG]http://img506.imageshack.us/img506/705/screenshotol6.png[/IMG]](http://imageshack.us)

---

### Post by RomeReactor on 2007-02-10
Did you run the [installer]("http://www.ubuntuforums.org/showpost.php?p=2098044&postcount=2")? If i remember correctly, it gives you the choice of browser to install to.

---

### Post by mekkah on 2007-02-10
Yes, i ran the installer in the terminal. Firefox was the only option. Oh well, since flash works correctly now in Firefox, i just converted my bookmarks & uninstalled Opera (i'll check back to it in the future).

Thanx for the help tough. At least i learned a new terminal command :lolflag:  Good thing there's so many friendly people here :KS

---

### Post by db9s on 2007-02-15
i am having the same problem with Opera, can't get myself to switch to firefox

---

### Post by aysiu on 2007-02-15
> **RomeReactor said:**
> now open a terminal and type

```
sudo nautilus
``` Use ```
gksudo nautilus
``` not *sudo nautilus*. *sudo* is for terminal applications (like Nano or Vim). *gksudo* is for graphical applications (like Gedit or Nautilus).

Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jourdanritchey on 2007-02-16
A quick FYI, copying from the Adobe download's installed libflashplayer.so (which seems to force you to install to /usr/lib/firefox/plugins/libflashplayer.so) to /usr/lib/opera/plugins/libflashplayer.so works well and is more universal than a user's /home directory.

I'm running Xinerama on 3 monitors, dual card, and when a site is running flash (browsing with Opera) I occasionally get a message pop-up saying that Opera has crashed, but it really hasn't and I just close the pop-up.  Haven't bothered to look into that yet - not frequent enough to bother me.

---

### Post by RomeReactor on 2007-02-16
> **aysiu said:**
> Use ```
gksudo nautilus
``` not *sudo nautilus*. *sudo* is for terminal applications (like Nano or Vim). *gksudo* is for graphical applications (like Gedit or Nautilus).

Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Thanks aysiu! Duly noted.

---

### Post by RYUTAZA on 2007-02-16
[COLOR="DarkOrange"]Kizz Kizz!!~[/COLOR]

:-k

---

### Post by RomeReactor on 2007-02-16
> **RYUTAZA said:**
> [COLOR="DarkOrange"]Kizz Kizz!!~[/COLOR]

:-k

?

---

### Post by poor_kenny on 2007-02-23
> **jourdanritchey said:**
> A quick FYI, copying from the Adobe download's installed libflashplayer.so (which seems to force you to install to /usr/lib/firefox/plugins/libflashplayer.so) to /usr/lib/opera/plugins/libflashplayer.so works well and is more universal than a user's /home directory.

I'm running Xinerama on 3 monitors, dual card, and when a site is running flash (browsing with Opera) I occasionally get a message pop-up saying that Opera has crashed, but it really hasn't and I just close the pop-up.  Haven't bothered to look into that yet - not frequent enough to bother me.
 
I tried that and got the same popup msg (and it kind of bothered me)! Anyway, I went back and looked at [Opera's plug-ins: Installation page]("http://www.opera.com/linux/docs/plugins/install/index.dml") and it says:
"Most Web browser plug-ins on the Linux platform today are made for Netscape. Opera supports most Netscape plug-ins through an Opera plug-in proxy called "libnpp". The proxy is included in the Opera package."

The "libnpp.so" file is located in that same directory (/usr/lib/opera/plugins) which probably causes a conflict of sorts and causes the message.

I looked at the "pluginpath.ini" file in ~/.opera and noticed that the path was "/usr/lib/mozilla/plugins" which in turn just contained a link to the /usr/lib/firefox/plugins directory. I changed that line to "/usr/lib/firefox/plugins" and that worked. The flash plugin then showed up in the "Open with plugin" dialog. 

The opera plugins.ini also had a line refering to the netscape/plugins directory (which also merely contained a link to firefox/plugins), I just deleted that line.

---

