---
title: "pbbuttonsd - Backlit Keyboard doesn't work"
date: 2005-08-04
forum: Apple PPC Users
---

### Post by Entity on 2005-08-04
Hello,

I have an 17" powerbook G4 (powerbook5,5.

Has someone managed to configure pbbuttonsd on that machine to enable the powerbook's keyboard backlit?

---

### Post by Entity on 2005-09-13
[QUOTE=Entity]Hello,

I have an 17" powerbook G4 (powerbook5,5.

Has someone managed to configure pbbuttonsd on that machine to enable the powerbook's keyboard backlit?[/QUOTE]

Running Breezy, I simply had to do the following :

sudo modprobe i2c-dev
sudo /etc/init.d/pbbuttonsd restart

Now it works.

---

### Post by asimaythink on 2006-08-01
Thank you! Works like a charm also in 6.06.

---

### Post by Entity on 2006-08-01
Since then, I've manage to find the answer I was looking for, thanks. ;-)

---

