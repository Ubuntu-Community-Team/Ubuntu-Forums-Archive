---
title: "A Few Questions"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by Dev'olution on 2006-08-11
Hey,

I've recently installed Ubuntu 6.06 and I have a few questions i'd like to ask...

1) How do you make shortcuts

2) How can i make a bar at the bottom similar to this -> [http://www.gnome-look.org/content/pre1/32768-1.jpg](http://www.gnome-look.org/content/pre1/32768-1.jpg)

Also, if anyone knows how to make a floating bar like in there, that would be appreciated...

3) I have a laptop with a resolution capability of 1200x800 and above... how can i get ubuntu to make the screen resolution up to that?

Thanks in advance,
Kris

---

### Post by Jagot on 2006-08-11
1) Right click wherever you want and click 'Create Launcher'.  It really depends on what you want to create a shortcut for as to what you put in there.

2) It just looks to me as if it's set not to fully expand by default.  Right click on the bottom panel and click 'Properties'.  Now untick the box which says 'Expand'.

3) It depends what graphics card you have.  Let us know and we can offer more advice.

---

### Post by Dev'olution on 2006-08-11
I have a SiS Graphics Card... so is there a SiS Graphics Controller? Like for Fedora Core 3

---

### Post by Jagot on 2006-08-11
From Terminal, try this:

```
sudo dpkg-reconfigure xserver-xorg
```

Should run you through setting up graphics.

---

### Post by Dev'olution on 2006-08-11
Cheers mate, just restarting now to see if theres any effect

---

