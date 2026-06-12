---
title: "2 problems, bugs or?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Virion on 2007-10-20
1. 3D Box effect - Mine is like a card. It didn't rotate like a box but flipped like a card. Is this something to do with my settings?
2. When I shutting down my computer, my screen shows "Out of Range". What does this mean?

Sorry the image quality ain't good because I took it with my mobile phone. (zoomed image)
[IMG]http://i229.photobucket.com/albums/ee199/leezhieng/Image011.jpg[/IMG]

Other than that, I haven't meet with any other problems yet. thanks.

---

### Post by TidusBlade on 2007-10-20
About the 3D box thing, Maybe check the settings of your 3D effects program, Beryl, Compiz, Fusion...
No idea about the Out of Range though :( I had it once, many months ago on Kubuntu but I forgot what I did... sorry

---

### Post by MonkeyBoy on 2007-10-20
The 3d box thing is an option in System>Preference>Appearance>Desktop Effects.  There are 3 settings in Gutsy: None, Normal, and Extra.  Extra is the setting with all the spinning box stuff etc.  Normal is a new setting that uses less resources but still looks cool.

---

### Post by shad0w_walker on 2007-10-20
The card slide thing is apparently the default in Gutsy, i guess it makes sense as the default number of desktops is only 2 so a cube isn't really practical with out giving an inconsistant experience (Flicking between 2-4 desktops)

Do you only get the out of range message during shutdown?

---

### Post by Perfect Storm on 2007-10-20
**1. 3D Box effect - Mine is like a card. It didn't rotate like a box but flipped like a card. Is this something to do with my settings?**
You need to install the compiz manager (can't recall the name of it.

**2. When I shutting down my computer, my screen shows "Out of Range". What does this mean?**

```
sudo nano /etc/usplash.conf
```
set the correct resolution (the bug is known and will be corrected very soon).
[ctrl]+[o]=save
[ctrl]+[x]=exit

---

