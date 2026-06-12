---
title: "Garbage???"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by neilmck on 2007-02-11
Can't help noticing a wad of 511MB being used by archived packages in /var/cache/apt/archives. Do I need to keep these or can I delete them and get new packages from synaptic?:) 

many thanks
Neil

---

### Post by jordanmthomas on 2007-02-11
```
sudo apt-get clean
```
will clean that right up for you.

---

### Post by jpeddicord on 2007-02-11
Another way to clean them out is inside Synaptic: Settings > Prefrences > Files > Delete Cached. :)

---

