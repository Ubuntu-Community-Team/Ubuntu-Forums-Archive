---
title: "how to install .bin files"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by doh224 on 2006-11-08
how do I install .bin files? :p

---

### Post by lucia_engel on 2006-11-08
Try this command while at the directory the file is in. Change filename to whatever name the bin file has.```
chmod +x filename.bin && ./filename.bin
```

---

### Post by doh224 on 2006-11-08
thanks :D

---

### Post by taurus on 2006-11-08
May want to put the sudo in front if you want to install it on your system, outside of $HOME!

```
sudo ./filename.bin
```

---

### Post by doh224 on 2006-11-08
what do you mean? could you maybe explane it a little better? ;)

---

### Post by PriceChild on 2006-11-08
> **lucia_engel said:**
> Try this command while at the directory the file is in. Change filename to whatever name the bin file has.```
chmod +x filename.bin && ./filename.bin
```That's pretty self explanatory...

Open a terminal, then
```
cd /path/to/wherever/the/bin/is
```then paste the above command, where filename.bin is the name of the file... change it ;)

---

### Post by doh224 on 2006-11-08
oki then. its installed but it does not work ;) ?

---

### Post by taurus on 2006-11-08
> **doh224 said:**
> oki then. its installed but it does not work ;) ?
Can you maybe explain it a little better?  ;)  What doesn't work and what are you trying to install?

---

