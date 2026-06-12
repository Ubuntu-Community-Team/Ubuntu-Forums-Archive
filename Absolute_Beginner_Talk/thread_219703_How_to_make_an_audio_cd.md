---
title: "How to make an audio cd"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-07-20
How do I burn mp3 files into an audio cd? KEB keeps saying unsupported format.

---

### Post by ThrobbingBrain66 on 2006-07-20
I think you mean K3B...

anyway, you must install the libk3b2-mp3 package through the konsole

```
sudo aptitude install libk3b2-mp3
```

---

### Post by mrvgarg on 2006-07-20
Thanks that worked. However the tracks are not showing up in order of their track numbers in tags.

---

### Post by OU812 on 2006-07-20
I think that no matter what burning app you use and no matter what platform (my experience anyway), the songs will always be alphabetical. To keep them in "album" order, you probably have to rename them with the track number at the beginning.

john

---

### Post by mrvgarg on 2006-07-20
Ok thanks

---

### Post by az on 2006-07-20
> **mrvgarg said:**
> Thanks that worked. However the tracks are not showing up in order of their track numbers in tags.

Serpentine and rhythmbox put them in order according to their id tags.

---

### Post by soze on 2006-07-21
> **azz said:**
> Serpentine and rhythmbox put them in order according to their id tags.

Really, how do you get that to work?
They both put them in filename order for me.

---

