---
title: "How to upgrade to a kernel with smp support?"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-11-26
I did a 'aptitude search kernel.*image' and what is returned are mainly kernel-image-2.4.* (about 18 of them), kernel-image-2.6, kernel-image-2.6-386, kernel-image-2.6-generic. Does it mean that the available debian packages for kernel 2.6 are only kernel-image-2.6, kernel-image-2.6-386 and kernel-image-2.6-generic? Is there any debian kernel package with smp support for P4 dual core?

Thanks :)

---

### Post by gord on 2005-11-26
```
 sudo apt-get install linux-686-smp 
```

that should install the 686 smp kernel for you :)

---

### Post by ranf on 2005-11-26
[QUOTE=Akhran]I did a 'aptitude search kernel.*image' and what is returned are mainly kernel-image-2.4.* (about 18 of them), kernel-image-2.6, kernel-image-2.6-386, kernel-image-2.6-generic. [/QUOTE]
Try `linux-image' in your search.

---

