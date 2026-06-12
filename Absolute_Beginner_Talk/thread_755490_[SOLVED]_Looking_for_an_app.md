---
title: "[SOLVED] Looking for an app"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2008-04-14
I'm looking for an app which would display my laptop temperature. Something nice and handy like the one in the screenshot. I saw it somewhere. It was added to the panel.

---

### Post by estaticd on 2008-04-14
[http://ubuntuforums.org/showthread.php?t=14730](http://ubuntuforums.org/showthread.php?t=14730)

That should fix you right up.

---

### Post by Inxsible on 2008-04-14
the screenshot that you have is probably of the weather applet. To get the CPU temp, you can install conky - which gives information about a lot of things and not just the cpu temp. Its also has a very small memory footprint.```
sudo aptitude install conky
```Make sure you have universe and multiverse enabled.

---

### Post by spiderbatdad on 2008-04-14
```
sudo apt-get install sensors-applet
```

Right click on a panel. Select 'add to panel.' Find 'Hardware Sensors."
Add it to the panel. Right click on it to configure the properties.

---

### Post by rkakkar on 2008-04-15
> **spiderbatdad said:**
> ```
sudo apt-get install sensors-applet
```

Right click on a panel. Select 'add to panel.' Find 'Hardware Sensors."
Add it to the panel. Right click on it to configure the properties.

its reporting my CPU temperature as 81 deg F. is that high?!

---

### Post by spiderbatdad on 2008-04-15
Mine runs at around 130F ouch it's hot!

---

