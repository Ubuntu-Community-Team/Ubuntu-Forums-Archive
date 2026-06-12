---
title: "Slow program loads"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by JengaBlocks on 2007-03-28
I don't know whether I am pushing it or what but my Ubuntu 6.10 system is pretty slow loading applications and I am wondering why. I've run RH 7.x on this box and application load times were definitely faster.

The box is a low end PII 266Mhz 384MB RAM (max for this mobo) with GeForce2 video card. Is there anything I can do on my end to speed this thing up? I realize this is an old computer but I'm trying to get the most out of it.

---

### Post by mahy on 2007-03-28
Please try Xubuntu instead. Perfect for your machine.

---

### Post by JengaBlocks on 2007-03-28
Oh no Mahy! It took me three days to get this system up and running ](*,) 

Everything from making 3 sets of Ubuntu CDs (Server, Alternate, Standard), to trying to get a WMP54G wireless card to work (that was frustrating as heck!). And I'm just a Linux newb for only three days (never used it before) and was about to toss the thing out the building!

But I'm more educated and better for it, huh :lolflag: 

Ok I'll consider it. Can you tell me where I can download it and why Xubuntu is suitable for my system?

---

### Post by mahy on 2007-03-28
> **JengaBlocks said:**
> Oh no Mahy! It took me three days to get this system up and running ](*,) 

Everything from making 3 sets of Ubuntu CDs (Server, Alternate, Standard), to trying to get a WMP54G wireless card to work (that was frustrating as heck!). And I'm just a Linux newb for only three days (never used it before) and was about to toss the thing out the building!

But I'm more educated and better for it, huh :lolflag: 

Ok I'll consider it. Can you tell me where I can download it and why Xubuntu is suitable for my system?

It's so simple!! Just run

sudo aptitude install xubuntu-desktop

and next time choose Xfce at graphical login. No clean installation necessary.

---

### Post by JengaBlocks on 2007-03-28
I went to Synaptic Package Manager and searched on "Xubuntu". Up came the following packages:

xubuntu-artwork
xubuntu-artwork-usplash *
xubunt-at-mag
xubuntu-at-speech
xubuntu-default-settings *
xubuntu-desktop *
xubuntu-docs *
xubuntu-system-tools *

I clicked on xubuntu-desktop 2.23 and marked it for installation. All the dependent packages marked with an asterisk above were also selected (89 packages 222MB, 2 removed). I then clicked on Apply and a lot of files were not fetched from us.archive.ubuntu.com.

Before applying, the ubuntu-desktop package and gnome-system-tools package warned me that they were going to be removed.


Something terribly wrong there with things out of synch.

---

