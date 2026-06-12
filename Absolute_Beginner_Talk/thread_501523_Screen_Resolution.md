---
title: "Screen Resolution"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by altonv on 2007-07-15
Hi,
Couple of days ago i installed Ubuntu Feisty Fawn, and everything worked perfectly. 
Today i decided to install Ubuntu Studio. Everything went well except Studio couldn't find my screen resolution. so i decided to go one step lower 800x600 and my screen just went blank. tried reloading a i still couldn't see anything. (goes blank after login)
i'm wondering if there is a fix with the recovery mode (Studio has no live cd)

Cheers.
Alton

---

### Post by w4ett on 2007-07-15
From the command prompt type:

sudo dpkg-reconfigure -phigh xserver-xorg

you can reset your GFX driver and resolution rates from there.

---

### Post by altonv on 2007-07-15
fixed.. thanks!!!

---

