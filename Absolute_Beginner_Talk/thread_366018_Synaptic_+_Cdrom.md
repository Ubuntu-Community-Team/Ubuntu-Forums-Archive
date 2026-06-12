---
title: "Synaptic + Cdrom"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by obelisk on 2007-02-20
I have an old dell laptop with a bad cdrom drive. I used a HP usb ext. burner to do my ubuntu install and figured I could download synaptic packages via the internet. Well now when I try to install particular packages it wants me to use the ubuntu cd and is defaulting to my bad cdrom drive...is there a way to change that default to my cdburner or the internet?

---

### Post by taurus on 2007-02-20
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and put a # sign in front of the first line with the CDROM in it.  That would comment it out so synaptic won't look for CD media when you run it.  Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by obelisk on 2007-02-20
Thanks now i'll be able to get packages to fix my next big challenge...wifi.

---

