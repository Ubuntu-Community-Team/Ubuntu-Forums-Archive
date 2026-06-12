---
title: "Just upgraded, and crashed desktop"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by NHmomma on 2007-12-22
Hi, I need help!  I just updated to 7.10, and upon restart, I get this black page... It states

Starting up.....
Loading, please wait....
Kinit:name_to_dev_t(/dev/dosl/by-uuod/f1762435-5053-4bc3-a763-f112088e217c) = S da2(8,2)
kinit: No resume image, doing normal boot.....

Ubuntu 7.10 mason-ubu-desktop tty1

mason-ubu-desktop login:


WHAT DO I DO!????!???  I think I lost everything!!!  Help!   I have not a clue what to do in this termial screen!

Carrie

---

### Post by taurus on 2007-12-22
Login with your username and password and perhaps reconfigure your X server again with

```
sudo dpkg-reconfigure xserver-xorg
```

Once done, see if you can restart X again with

```
startx
```

---

### Post by NHmomma on 2007-12-22
Trying that right now!  Thanks!

---

### Post by NHmomma on 2007-12-22
It worked, now tweaking video/monitor settings to get my resolution back to what I had.   

Thanks for the quick answer!

Carrie

---

