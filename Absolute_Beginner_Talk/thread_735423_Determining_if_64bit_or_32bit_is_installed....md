---
title: "Determining if 64bit or 32bit is installed..."
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by howejustin on 2008-03-25
Hi,

I installed Gutsy Ubuntu (7.1) a couple months ago, but forgot if I used the 32 bit installer or 64 bit. My AMD is a 64 bit proc, so I'd like to make sure I have the correct Ubuntu installed as well. Is there a way to check this besides going into my recent updates to see if it pulled them from some 64 bit repository?

---

### Post by OffAxis on 2008-03-25
try 
```
uname -a
```

or

```
dpkg --print-architecture
```

---

### Post by heartburnkid on 2008-03-25
My understanding is that, even if you do have a 64-bit proc installed, it's usually better at this point to go with the 32-bit distro.  You lose some performance, but you gain stability and compatibility.

I may be wrong about this though.

---

### Post by Paqman on 2008-03-25
> **heartburnkid said:**
> My understanding is that, even if you do have a 64-bit proc installed, it's usually better at this point to go with the 32-bit distro.  You lose some performance, but you gain stability and compatibility.

I may be wrong about this though.

I'm sure most 64-bit users would disagree with this. 64-bit used to be a hassle, but now there are almost no issues. Most people report a 100% positive experience with 64-bit.

Personally, I don't see any reason to throttle a modern chip by restricting it to 32-bit.

---

### Post by heartburnkid on 2008-03-25
Ah, perhaps I should switch to 64-bit when I upgrade to Hardy then.

Nothing to see here, just clueless noobism. :)

---

### Post by tribaal on 2008-03-25
The old 32bits against 64bits debate...

I'm using 100% 64bits and have _no issues_ at all. And I do a lot of gaming, I use my PC as a media center and watch videos all the time :)

My 2 cents: go with 64bits and leave the others in the past.

- Trib'

---

### Post by howejustin on 2008-03-25
Thanks for the info, looks like I'm already on 64 bit. No problems yet...

```
justin@justin-ubuntu:~$ uname -a
Linux justin-ubuntu 2.6.22-14-generic #1 SMP Tue Feb 12 02:46:46 UTC 2008 x86_64 GNU/Linux

```

---

### Post by Paqman on 2008-03-25
> **heartburnkid said:**
> Ah, perhaps I should switch to 64-bit when I upgrade to Hardy then.

Nothing to see here, just clueless noobism. :)

Well, in the world of Windows, you're completely right. 64-bit support is bad, so the smart advice for Windows users is to stick to 32-bit for now.

However, us Linux-using weirdoes have it a lot better.

---

### Post by fissionmailed on 2008-03-25
> **heartburnkid said:**
> My understanding is that, even if you do have a 64-bit proc installed, it's usually better at this point to go with the 32-bit distro.  You lose some performance, but you gain stability and compatibility.

I may be wrong about this though.

I personally use a 64 bit OSs on my laptop.  I've never had a problem. I'm not the most experienced user or have been using it THAT long(2-3 months). YMMV

---

### Post by Azureskies on 2008-03-25
AMD 64 bit chips can process 32 bit OS's and programs, so you should be fine.

---

### Post by joshrobinson on 2008-03-25
are java, flash, and firefox working good together now in 64bit? or are they still a hassle to install and get running

---

### Post by LoRD_TRiFLe on 2008-03-27
I installed the 32 bit version a while back.  Is it possible to upgrade to the 64 bit version, or will have to reinstall from scratch?

---

