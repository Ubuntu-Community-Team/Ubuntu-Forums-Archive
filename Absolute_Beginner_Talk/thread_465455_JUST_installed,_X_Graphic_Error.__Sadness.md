---
title: "JUST installed, X Graphic Error.  /Sadness"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by sochbat on 2007-06-05
So i tried using the Live CD to mess around with ubuntu, worked perfectly.  Once i installed, it'd ask which device to boot from, and i choose the drive with ubuntu on it.

Mentions something about X Graphics not being set up, all that bad stuff.  I'm searching threads to no avail.  What the deuce?

I've searched under "nvidia x graphic", "nvidia" "x graphic", and a whole lotta other key terms, and nothing.  I really wanted to play with ubuntu before work too.  Shucks.

Any help?

PS.  Its an Nvidia GeForce4 MX44-0-8X AGP.

---

### Post by taurus on 2007-06-05
You need to configure X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by sochbat on 2007-06-05
I've gotten to the GUI thanks to some help from TeXXon, in the IRC chat.  MADDD rep to you.  I'm currently updating drivers, and all that stuff.

---

