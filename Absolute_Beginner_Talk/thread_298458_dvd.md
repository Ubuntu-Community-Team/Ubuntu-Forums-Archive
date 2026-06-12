---
title: "dvd"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by manas on 2006-11-12
Is there any way I can play dvd on Ubuntu. trying since morning. loaded automatix2 with all other media player none worked.


help me](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by MrKlean on 2006-11-12
Just wondering...did you load the aud-dvd codecs from Automatix ???

---

### Post by DannyG on 2006-11-12
The following commands will install the codecs required for viewing encrypted files and DVD's.

```
wget -c -O /tmp/w32codecs.deb http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
```
```
wget -c -O /tmp/libdvdcss2.deb http://www.debian-multimedia.org/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb
```
```
sudo dpkg -i /tmp/w32codecs.deb /tmp/libdvdcss2.deb
```

---

### Post by manas on 2006-11-12
Mr Klean I have loaded aux-codecs from Auotmatix2

DannyG thanks for the script. After runing the script I try play dvd it did not work.

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

