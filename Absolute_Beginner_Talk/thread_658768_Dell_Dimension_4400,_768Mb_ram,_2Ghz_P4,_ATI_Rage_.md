---
title: "Dell Dimension 4400, 768Mb ram, 2Ghz P4, ATI Rage 128, ati driver - graphics slow"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2008-01-05
The title pretty much sums it up - I have got this person running Ubuntu 7.04 and they love it and would not go back to windows ever, but although 3D is technically enabled, all things, like even moving a window, and of course actual 3D is rather slow.  They don't mind for the time being, and will not use 3D ever, but things like scrolling through a web page, or moving a window shouldn't be slow! I would like some help with getting this to work, the current driver is "ati", the card is a ATI Rage 128 (might be Pro, and AGP), and restricted driver manager says one is unnecessary, and desktop effects (old compiz) "can't" enable.

Keep in mind this person is very, "average" ;) computer user, and my ability to help them is limited to connecting through remote desktop, and in person in summer and Christmas... ](*,)

---

### Post by oliviacond on 2008-01-05
what about fglrx?

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

---

### Post by ryanVickers on 2008-01-05
ok, I'll try that :D

um, what exactly does it do though?..... :rolleyes:

---

