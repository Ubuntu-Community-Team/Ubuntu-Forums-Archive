---
title: "How to remove microsoft fonts?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-04-29
I installed the "ubuntu restricted extras' package and it also installed the microsoft fonts.  How can I remove the microsoft fonts?

---

### Post by Metacarpal on 2007-04-29
You'll need to remove the packages msttcorefonts ttf-xfree86-nonfree (note: doing this will remove the "restricted extras" package, but that's just a meta-package - basically, a box the other packages were shipped in).

You can remove them through Synaptic (System menu > Administration > Synaptic Package Manager)
or through the terminal (Applications menu > Accessories > Terminal):
```
sudo aptitude remove msttcorefonts ttf-xfree86-nonfree
```

---

### Post by nanotube on 2007-04-29
> **Matt1632 said:**
> I installed the "ubuntu restricted extras' package and it also installed the microsoft fonts.  How can I remove the microsoft fonts?

you mean the package "msttcorefonts" ?
if so, the list of fonts is stored in a textfile here:
/var/lib/msttcorefonts/ms-fonts
and the actual fonts are in 
/usr/share/fonts/truetype
so... just delete those. 

unless someone has a better idea... :)

---

### Post by nanotube on 2007-04-29
> **Metacarpal said:**
> You'll need to remove the packages msttcorefonts ttf-xfree86-nonfree (note: doing this will remove the "restricted extras" package, but that's just a meta-package - basically, a box the other packages were shipped in).

You can remove them through Synaptic (System menu > Administration > Synaptic Package Manager)
or through the terminal (Applications menu > Accessories > Terminal):
```
sudo aptitude remove msttcorefonts ttf-xfree86-nonfree
```

will this also remove the ms fonts that are downloaded by msttcorefonts from the web during installation?

---

