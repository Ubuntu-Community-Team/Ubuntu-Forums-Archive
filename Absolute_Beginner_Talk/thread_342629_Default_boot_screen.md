---
title: "Default boot screen ?"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-01-20
I tried out KDE instead of Gnome, but I decided to switch back to Gnome.

The problem is that the Kubuntu logo + blue text remains when I boot up. Does anyone know how to change it back to the default Ubuntu logo + text??

Thanks

---

### Post by taurus on 2007-01-20
Maybe

```
sudo aptitude update
sudo aptitude remove kdm
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```
Or reboot.

---

### Post by kbsuperstar on 2007-01-20
I'll give it a try. Thanks :D

---

### Post by kbsuperstar on 2007-01-20
No, it didn't work. Any other ideas?

---

### Post by Tiede on 2007-01-20
You need to revert back to the default artwork. Try in a terminal ```
sudo apt-get install ubuntu-artwork
``` and you should get your ubuntu-flavors back :D

---

### Post by kbsuperstar on 2007-01-20
No dice ](*,) 

Any more ideas :(?

---

### Post by JamieC on 2007-01-20
Try this in terminal:
```

sudo cp /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`

```

Post the output after dpkg-reconfigure has finished, please.

---

### Post by kbsuperstar on 2007-01-20
Woohoo, it worked! Thanks so much!!

---

### Post by JamieC on 2007-01-20
You're welcome, I had the same problem after installing the kubuntu-desktop and xubuntu-desktop meta-packages. It's easy when you know how, I guess!

---

### Post by CroEragon on 2007-01-23
Just note to anyone who might use this thread to help himself (as i did).

```
sudo cp /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`
```

This command didn't work for me, i had to modify it a bit. On my system there is no usplash-default.so so command returned error. Insted, in given folder i found usplash-theme-ubuntu.so so i changed first part of command to point to that file. So now it looks like this:
```
sudo cp /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`
```
Hope it will help somebody.

---

