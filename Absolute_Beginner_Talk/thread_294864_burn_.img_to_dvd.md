---
title: "burn .img to dvd?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-11-07
Hello i wounder how to mount an .img file or how to burn an .img file to a dvd disc and watch it on my dvd player?

---

### Post by taurus on 2006-11-07
```
sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.img /mnt/iso
```
And if you want to burn it, burn it as a DVD image file because basically, .img is the same as .iso...

---

### Post by timmeeej on 2006-11-07
right click the .img file => burn to dvd

or something like that, i'm not sure because i'm not on ubuntu right now (@work)

---

### Post by haxer on 2006-11-07
but last time i did that right click and select burn to... my sound was all weird on the dvd but is that becuse the quality of the .img file "dvd" is bad?

---

### Post by taurus on 2006-11-07
You can check it before you burn by mounting it and watching it with xine!!!

One more time...
```
sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.img /mnt/iso
xine dvd://mnt/iso

```
And if everything is good, fire up k3b and burn it as a DVD image disc...

---

### Post by haxer on 2006-11-07
Nice thx :)

---

### Post by taurus on 2006-11-07
> **haxer said:**
> Nice thx :)
See how easy it was!!!  ;) 

In fact, you can even play it directly without mounting it first if you choose...

```
gmplayer <filename>.img
-or-
gmplayer <filename>.iso
```

---

