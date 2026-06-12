---
title: "GCC missing"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by CurlyBlue on 2006-08-31
Hi

can anyone help me

Am in the process of installing a HP 2600n Color Laserjet and when I try and run make I get the following:

#
# Dependencies...
#
      ***
      *** Error: cc is not installed!
      ***
      *** Install Software Development (gcc) package
      ***
make: *** [all-test] Error 1

Any ideas how I fix / resolve this.

Thanks

:confused: :confused:

---

### Post by Bachstelze on 2006-08-31
```
sudo apt-get install build-essential
```

---

### Post by CurlyBlue on 2006-08-31
Yoo D'Man!

Thx

---

### Post by FenrisAbraxas on 2006-08-31
> **HymnToLife said:**
> ```
sudo apt-get install build-essential
```

Im still wondering if the package is "build-essential" why they arent installed by default? :S

---

### Post by tribaal on 2006-08-31
I guess not everyone needs to build applications... Most people just go with the packages, which is fine for most cases.

Well I guess :)

- trib'

---

### Post by jpeddicord on 2006-08-31
> **FenrisAbraxas said:**
> Im still wondering if the package is "build-essential" why they arent installed by default? :S
Most likely it won't fit on the CD. :D

---

