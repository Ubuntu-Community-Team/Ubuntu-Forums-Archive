---
title: "ATI Radeon x700 problem"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by odessa on 2007-10-31
I am fresh to Ubuntu, tryed it on my spare computer, a week and decided i wanted to do it on my main computer, but!!

I can't get the driver for my graphic card to work

i downloaded a program Envy, that was supposed to fix it, i tryed at the command promt


"The software source for the package  xorg-driver-fglrx  is not enabled."

is the message I get when i click on it in the restricted driver manager

my graphic card is ATI Radeon x700 and I have toshiba laptop

---

### Post by Pumalite on 2007-10-31
sudo apt-get install xorg-driver-fglrx

---

### Post by overdrank on 2007-10-31
> **odessa said:**
> I am fresh to Ubuntu, tryed it on my spare computer, a week and decided i wanted to do it on my main computer, but!!

I can't get the driver for my graphic card to work

i downloaded a program Envy, that was supposed to fix it, i tryed at the command promt


"The software source for the package  xorg-driver-fglrx  is not enabled."

is the message I get when i click on it in the restricted driver manager

my graphic card is ATI Radeon x700 and I have toshiba laptop

Hi and if you are using Gutsy then I would recommend looking to make sure all repos are enabled. System, administration, software sources. Good luck!

---

### Post by odessa on 2007-10-31
i get this message in the promt

E couldt find package xorg-driver-fglrx

---

### Post by sloggerkhan on 2007-10-31
Off a clean install while connected to internet install it through the restricted driver manager in system>admin.

---

