---
title: "Media and Installtion problems"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by weaboo on 2007-03-28
I try to play any kind of media but it simply doesnt work. A dvd, or a song, or internet downloads. i keep getting error messages.

And i am unable to install anything.

I keep getting dpkg-- configure -a and in synaptic when i choose install it says unable to do so. 

Please help i really like ubuntu right now and i would love to get it working.

---

### Post by seshomaru samma on 2007-03-28
did you try to install something and it went wrong?
what happens when you run :
```
sudo apt-get install -f

```

---

### Post by weaboo on 2007-03-28
i get 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by oilchangeguy on 2007-03-28
ok, go to applications, accessories, terminal, and type in the error message (dpkg --configure -a) without (), and press enter.

---

### Post by weaboo on 2007-03-28
That is what i got.

dpkg: requested operation requires superuser privilege

so i went into the root termonal did that and nothing came up

---

### Post by zvacet on 2007-03-29
```
sudo dpkg --configure -a
```

---

