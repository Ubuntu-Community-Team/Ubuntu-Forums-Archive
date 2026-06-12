---
title: "Wifi Setup Under Ubuntu"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by radicaldreamer on 2007-03-12
Ok, I was using Breezy Badger for over a year and decided to make the leap to 6.10, well, i did it via command line and my install would fail to boot any longer so i downloaded the full 6.10 and installed from scratch. Now for some reason I cant get my wifi working any more, I have both a built in dell wireless card on my inspiron 8200 as well as a cisco pcm 350 and Im not sure what i am doing wrong.

I go to networking and put a check in enable this connection on all devices listed and put in my ssid which has no encryption and no security of any kind (open wifi)

Is there something else I should be doing?

---

### Post by radicaldreamer on 2007-03-12
Bump

---

### Post by NeoGreen on 2007-03-12
Do you remember how you configured your wireless card when you first installed 5.10.  You may have to do the same thing.  You know install ndswrapper, then the driver, then activate it.  I had  to do the same when I upgraded from 5.10 to 6.10.

---

### Post by pearlie on 2007-03-12
Hmmm - try installing [Wicd]("http://compwiz18.blackhole.cx/wicd/wb/") and see if you can configure and connect.  I use ndiswrapper, and I've had issues with configuring wireless using the default network manager and wifi radar, but Wicd worked for me.

---

### Post by Kobalt on 2007-03-12
Before starting to tweak your config and everthing, let's check if your card is recognsised and set up at least. Can you please post the output of :
```
iwconfig
```

---

