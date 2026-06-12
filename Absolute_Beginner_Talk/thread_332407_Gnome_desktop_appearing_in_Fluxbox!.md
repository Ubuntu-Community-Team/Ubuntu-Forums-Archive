---
title: "Gnome desktop appearing in Fluxbox?!"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by jem7v on 2007-01-06
This is probably the most bizarre issue I've ever had with Fluxbox. It hasn't happened with previous installations, but it did This time, obviously.
I compiled the latest version of Fluxbox from source, as explained in [http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759) and it went smoothly, but once I started using it, something strange happened:

Randomly, the fluxbox desktop disappears and is replaced with my Gnome desktop... i.e., the background image changes back to the one I was using in Gnome earlier, and the icons in my ~/Desktop folder appear on the desktop, and right-clicking on the desktop brings up the normal Gnome desktop right-click menu instead of the Fluxbox menu, and the Fluxbox menu at the bottom of the screen vanishes.

What in the world is going on? Ideas, anyone?

---

### Post by tbroderick on 2007-01-06
Are you running nautilus by any chance? If you run nautilus outside of GNOME, you should use;

```
nautilus --no-desktop
```

---

### Post by jem7v on 2007-01-06
Interesting! I'll give that a try.

---

### Post by jem7v on 2007-01-06
Doot doot doo, looks like that may have solved it! I think. Maybe. Unless it was something else doing it... but that seems to be the likely solution! Thank you.

---

### Post by heathen on 2007-01-08
it took me a while to figure that out...  

is there anyway to get nautilus to run from the menu via the --no-desktop option??  I've tried a few difrerent things and they havent worked...   (other browsers than nautilus are a viable option for me)

---

### Post by jem7v on 2007-01-08
Yes! This is what I did. Just use this code in your ~/.fluxbox/menu file:
```
[exec] (Nautilus) {nautilus --no-desktop}
```

---

### Post by heathen on 2007-01-08
lol... thanks...  it didnt work for me because I cant type...

---

