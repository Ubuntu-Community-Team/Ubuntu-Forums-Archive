---
title: "How can I see how much space I have left on a partition in KDE?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Dave_Man on 2006-10-03
I have an annoying problem, 

I have looked everywhere and checked all the settings pages but can't find a way to see how much free space I have left on a specific partition!

In Gnome, I don't have that problem, but in KDE, for some reason it just doesn't show it anywhere.
pretty irritating.

anybody have a solution?
I've tried searching the forums but couldn't find anything about this.

Thanks.
Dave.

---

### Post by seijuro on 2006-10-03
Kmenu -> system -> KinfoCenter -> Partitions

---

### Post by Bachstelze on 2006-10-03
```
df
```

---

### Post by jaboua on 2006-10-03
```
df -h
```
Same as above, but easier to read for humans

---

### Post by andiii on 2006-10-03
I would use df -H, it gives you more free space. 

:mrgreen:

---

### Post by Dave_Man on 2006-10-03
Ok, how do I do it in Konqueror so I don't have to open a terminal or the control panel each time?

A simple right click and properties would be nice, but i've tried that a hundred times.

Thanks for the response.
Dave.

---

### Post by jaboua on 2006-10-03
Well, seems like you answered your own question. Right click and properties, wait a couple of seconds for calculating and watch the bottom of the "General" tab - there is "Free disk space".

---

### Post by Dave_Man on 2006-10-03
haha, i've done it a hundred times and never saw it.

The reason is that it only shows it when you are browsing through /something
but when you are seeing the same folder through media:/ it shows nothing!

I have no idea what the diffrence is, but thats it.

Thanks, 
Dave.

---

