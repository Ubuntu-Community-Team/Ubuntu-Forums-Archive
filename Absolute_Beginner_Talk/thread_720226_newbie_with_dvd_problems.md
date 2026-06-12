---
title: "newbie with dvd problems"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by jpw111163 on 2008-03-10
i need help . i cant seem to play a dvd at all i very new to this so do i need a plug in and how do i install it ? im trying to teach this old dog some new tricks :lolflag:, like what i have seen so far ,

---

### Post by ibizatunes on 2008-03-10
[http://tuxenclave.wordpress.com/2008/01/03/how-to-enable-multimedia-suport-in-ubuntu-710/](http://tuxenclave.wordpress.com/2008/01/03/how-to-enable-multimedia-suport-in-ubuntu-710/)

may fix your problems

---

### Post by jpw111163 on 2008-03-10
thanks i will have a read

---

### Post by jan quark on 2008-03-10
also check out this guide it worked for me:

run this in the terminal, just copy and paste and hit enter:

```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```

then run this:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

now open the application gxine and you should be able to watch you dvd

---

### Post by jpw111163 on 2008-03-10
thank you very much with the first i got sound but no pic so i did second and my dvd now works a treat thanks

---

