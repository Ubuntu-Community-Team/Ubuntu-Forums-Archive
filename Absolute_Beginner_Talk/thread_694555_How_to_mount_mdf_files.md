---
title: "How to mount mdf files ?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Joor on 2008-02-12
Can someone help me mounting this image of a CD..its a mdf file, so programs like Gmount doesnt work :(

---

### Post by jan quark on 2008-02-12
give this a try

[http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html](http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html)

---

### Post by kpkeerthi on 2008-02-12
[http://mdf2iso.berlios.de/](http://mdf2iso.berlios.de/)
Not sure if it is in ubuntu repo.

---

### Post by Joor on 2008-02-12
> **jan quark said:**
> give this a try

[http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html](http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html)

Does it work on 64bit ubuntu ?

---

### Post by Joor on 2008-02-12
Acetone didnt work since I cant instal it.
I dont know how to install The mdf2iso program, can you help me ?

---

### Post by kpkeerthi on 2008-02-12
I figured it is in ubuntu repo. Open a terminal and type
```
sudo aptitude install mdf2iso
```

Usage should be straightforward 
```

mdf2iso mdf.file iso.file

```

```
man mdf2iso
```

---

### Post by bulletxt on 2008-02-12
AcetoneISO does work you just need to compile it from sources as for sure you downloaded the x86 32-bit binary pack :)

---

