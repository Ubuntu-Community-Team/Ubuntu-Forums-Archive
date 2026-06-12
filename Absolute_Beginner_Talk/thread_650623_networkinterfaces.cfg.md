---
title: "network/interfaces.cfg"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by doughardy on 2007-12-26
running a ubuntu  2.6.20-16-server

hi guys ive deleted by mistake my interfaces.cfg file  silly  i know  could some one help me on how to reinstall it please or if anyone has a interfaces.cfg i could copy that would be very nice  thx all

---

### Post by Hospadar on 2007-12-26
If you're using a wired connection, it's super easy
try doing ```
sudo nano /etc/network/interfaces
```and then just add in the loopback and eth0 interfaces so your file looks like```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

``` and then you should be able to ```
sudo ifup eth0
``` or just restart your machine.

Also if you don't know how to use nano Ctrl-o saves, Ctrl-x quits (you could use whatever editor you want though of course

If you have wireless it's a little trickier and depends on what sort of card and encryption you are using, but if you google for it I'm sure you can locate some info.  Also if you are configuring wireless, you can list neworks from the command line with ```
iwlist scan
```

---

### Post by doughardy on 2007-12-26
exellent hospidar all sorted now  thankyou very much:popcorn:

---

