---
title: "[SOLVED] What is the software source for xorg-driver-fglrx package ?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Google Spider on 2008-03-09
Hi,

I am on Kubuntu trying to install restricted driver for ATI radeon xpress 200. I already added these software sources:

cannonical supported open source software (main)
community maintained oss (universe)
propritery drivers for devices (restricted)
software restricted by copyright or legal issues(multiverse)
source code

Screenshots attached (hopefully)

When I try to enable the driver from restricted driver manager, it tells me that I have not added the software source for 'xorg-driver-fglrx'.
Can you pleases tell me what to do ?

Many thanks.

---

### Post by mikeyphi on 2008-03-09
Open System/Administration Synaptic Package Managed and click on 'reload'
Then use the search box to find xorg-driver-fglrx
tick the box and then click on Apply.

Before you do that try the Restricted Driver Manager again - it could be that your package file hadn't been updated.

---

### Post by Google Spider on 2008-03-09
Thanks. It worked! :D

and sorry for asking such a basic question. I'm a n00b

---

