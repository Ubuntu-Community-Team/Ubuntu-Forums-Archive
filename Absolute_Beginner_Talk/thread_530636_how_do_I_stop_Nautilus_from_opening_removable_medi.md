---
title: "how do I stop Nautilus from opening removable media?"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by jon.reeve on 2007-08-20
Every time I insert my removable hard drive, which has 2 partitions, the XFCE file manager Thunar and the GNOME file manager Nautilus both open up windows displaying the contents of both partitions, so that makes four windows that I then I have close. Is there a way of disabling the auto-open feature, or whatever it might be, at least in Nautilus?

---

### Post by Dr Small on 2007-08-20
Did you try going to System > Preferences > Removable Devices and Media and look around in there?

Dr Small

---

### Post by Hobo Joe on 2007-08-20
While were on the subject, I'd like to know how to change the programs that start up based on what I put it. At the moment, when I put in a DVD, it opens in Totem, but I would like it to open in VLC, and media players open in rythmbox, but I would like them to open in Amarok.

Right now the commands are:
```

totem %m

and 

rhythmbox

```
Should I just change it to look like this?
```

vlc %m
amarok

```

Or would that not work?

---

### Post by Dr Small on 2007-08-20
I have never tried it, but I don't see where it would hurt it if you tried. If it really messes up, just put it back to what it was on, or try some more expiramenting.

Dr Small

---

### Post by jon.reeve on 2007-08-20
> **Dr Small said:**
> Did you try going to System > Preferences > Removable Devices and Media and look around in there?

Well, I used to see that in GNOME, but since downgrading to Xubuntu and the XFCE environment, I don't have that option in my system preferences anywhere. Is there a command to access that via Alt+F2?

---

### Post by Dr Small on 2007-08-20
You could try:
```
gnome-volume-properties
```

Dr Small

---

### Post by pixatintes on 2007-08-22
Thanks Dr.Small is this. :lolflag:

---

