---
title: "How to Capture Screenshot with Dropdown Menu in Place?"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by OldDogNewTricks on 2006-02-06
Screenshot is cool, but I can't figure out how to make it capture an image of the desktop with a dropdown menu in place.  The Screenshot app closes the dropdown menu before it takes the snapshot.  Any ideas?

---

### Post by kaamos on 2006-02-06
You can do this with an app called scrot. Install with synaptic or with
```
sudo apt-get install scrot
```
you use it from the terminal like this
```
scrot -cd 5 ~/Desktop/screenshot.png
```
The number after -cd is the delay in seconds

---

### Post by aysiu on 2006-02-06
If you're in Gnome, Alt-F2 ```
gnome-screenshot --delay 5
```

If you're in KDE, KSnapshot has this functionality built-in (and it's point-and-click).

---

### Post by OldDogNewTricks on 2006-02-06
Thanks guy!  This forum and its supports are awesome.

---

### Post by Michael Steinberg on 2006-02-06
Or you could use the GIMP screenshot & minimize the GIMP in the time-delay, before you drop that menu down....

---

