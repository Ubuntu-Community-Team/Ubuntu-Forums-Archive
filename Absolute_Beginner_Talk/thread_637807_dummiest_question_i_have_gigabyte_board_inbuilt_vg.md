---
title: "dummiest question i have gigabyte board inbuilt vga is it ati or nvida drive"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by ninja_2405 on 2007-12-11
dummiest question i have gigabyte board inbuilt vga is it ati or nvida drive having problem while enabling compiz  someone please help:(:(:(:(:(:(:(

---

### Post by forestpixie on 2007-12-11
try this in a terminal```
lspci
```

---

### Post by mcduck on 2007-12-11
Impossible to say without knowing the actual model of the motherboard.

But try running 'lspci | grep VGA', that might tell you what the graphics chip is.

---

### Post by ninja_2405 on 2007-12-11
thak u so much 

 #lspci | grep VGA

 01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

this is wht i get

---

