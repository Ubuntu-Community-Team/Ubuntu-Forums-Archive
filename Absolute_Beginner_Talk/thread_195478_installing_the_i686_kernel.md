---
title: "installing the i686 kernel"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by lordharsha on 2006-06-12
I've downloaded the linux-686 kernel. How do I install it? I figured out that you have to use 'installkernel', but I can't figure out how.

---

### Post by uzi09 on 2006-06-12
just use apt to install it
```

sudo aptitude install linux-image[tab][tab]

```

where it says [tab] press tab there. this way it'll show you the different linux kernels and just finish off the name with whichever kernel you want.

i believe the name is:
linux-image-2.6.15-23.i686

---

### Post by 23meg on 2006-06-12
```
sudo apt-get install linux-image-686
```

---

### Post by lordharsha on 2006-06-13
Thanks. And what's the difference between linux-image-686 and 
linux-image-2.6.15-23.i686

---

### Post by 23meg on 2006-06-13
linux-image-686 is just a metapackage that installs the latest available 686 kernel, in this case linux-image-2.6.15-23-686. Thus ```
sudo apt-get install linux-image-2.6.15-23-686
```would have done the same.

---

### Post by lordharsha on 2006-06-13
Oh, ok. thanks. I got the new kernel and it's working fine

---

### Post by beatyou on 2006-06-21
[QUOTE=23meg]```
sudo apt-get install linux-image-686
```[/QUOTE]

Thanks meg, this is exaclty what I was looking for. I was previously running the i386 kernel but this did the trick to update to 686.

---

