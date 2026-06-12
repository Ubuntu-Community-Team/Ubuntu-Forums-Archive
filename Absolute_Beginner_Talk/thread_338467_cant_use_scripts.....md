---
title: "cant use scripts...."
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by L_o_N_e_R on 2007-01-14
they were working fine before...

then the script folder got erased...so i made a new one

but when i put the scripts there i cant use it..

heres are the scripts im using...

[http://www.debianadmin.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.debianadmin.com/mount-and-unmout-iso-images-without-burning-them.html)

they wont appear in the script colum when i right click...

---

### Post by taurus on 2007-01-14
If you want to mount an ISO image, you can still do it from a terminal!

```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop **filename.iso** /media/iso
```

---

