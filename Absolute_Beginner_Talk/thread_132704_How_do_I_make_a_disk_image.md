---
title: "How do I make a disk image"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by jwalk on 2006-02-18
Hi all, I'm a long time windows user first time linux user. I have several computers with the same hardware that I would like to install ubuntu 5.10 to donate to low income students. I have installed 5.10 on 1 pc and installed several packages using the SPM. I would like to be able to burn this image onto a boot cd so I can quickly install it on all the others. Does anyone know of a way to do this?

---

### Post by Clark Nova on 2006-02-18
You could do this using a program like Symantec Ghost, it's what we use at work for this very kind of thing but I'm not sure if there is something similar which is open source. I'm sure a more experienced user will be able to advise you of something though :)

---

### Post by jwalk on 2006-02-18
Thanks, I have Ghost available to me but was looking for something open source. I'm trying to learn new/different technologies to advance my knowledge but at the same time provide a community service

---

### Post by Clark Nova on 2006-02-18
[QUOTE=jwalk]Thanks, I have Ghost available to me but was looking for something open source. I'm trying to learn new/different technologies to advance my knowledge but at the same time provide a community service[/QUOTE]

I've never used this myself but this looks like it might do the job for you:

[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

### Post by zac1333 on 2006-02-18
I've used G4U, works great, if you have any questions just PM me.

---

### Post by cotcot on 2006-02-19
The Open Source alternative to Ghost is "partimage" ( [http://www.partimage.org/](http://www.partimage.org/) ).
Partimage allows you to clone computers. Please read some howtos and tutorials about it. I use the Kanotix live CD to copy partitions to an external HDD. You can also copy to a DVD (or more DVDs). There are some restrictions. The source computer architecture should not differ too much from that of the computers to be cloned and the partitions on the cloned computers must be equal or larger than those of the source computer. The documentation explains it.

---

### Post by patrick295767 on 2006-02-19
U can use dd from the knoppix bootable cd 
u can then mount from the network to ur present installed pc via nfs: 

After sharing one folder on ur "server" pc .... (bla bla) (/mnt/sharedfolder for instance)
(exports allow autofs ... )
   
```
dd if=/dev/hda bs=1k conv=sync,noerror | gzip -9 > /mnt/sharedfolder/image-backup.img.gz
```
   
 On the new pc, booted with knoppix cd:
  ```
mkdir /mnt/server
mount -t nfs server:/mnt/sharedfolder /mnt/server
gzip -dc /mnt/server/image-backup.img.gz | dd of=/dev/hda
```
  
  (that's a quick example)
  
Enjoy Linux ! :-)
  
Patrick

---

