---
title: "where can I find which graphic card im using :S"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by alket on 2007-08-30
where can I find which graphic card im using :S

its noob question but i really cant find it hehe

---

### Post by tuxcantfly on 2007-08-30
> **babaroga said:**
> where can I find which graphic card im using :S

its noob question but i really cant find it hehe

you can either crack your case open to see, or use this command:
```

cat /etc/X11/xorg.conf | grep Device | tail -1
```

---

### Post by justleen on 2007-08-30
```
lspci |grep -i graphic 
``` gives some more detail

---

### Post by jay4e on 2007-08-30
xorg.conf will give you your driver and that might give you some info.
```
sudo scanpci
```
will give you the manufacturer as well as the pci vendor and device id which might be able to look up on ([www.pcidatabase.com](www.pcidatabase.com)).  

cracking it open if its a desktop is the best way to be sure exactly what card your runing.  if its a laptop or a factory system just check the manufactures website.  there are other ways to find out but no program is 100% and likely only give you an idea of what card it is. 

so the question is why do you need to know?

---

### Post by justleen on 2007-08-30
cracking it open is not always the best way... i can recall several occasions that i found my self with brandless hardware, or unlabeled chipsets :)

---

