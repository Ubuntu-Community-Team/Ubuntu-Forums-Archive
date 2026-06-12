---
title: "How do I get my wireless card working"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Squish on 2008-02-23
I have a Linksys wmp54gx4 wireless card in my computer,  but it does not work.

I dont know what I need to do to make it work.
I am running Ubuntu Studio amd64 7.10
and it is a fresh install, which does not, and can not get internet.

Right now, I am using my ipod to transfer files to it, but It needs wireless on its own... drastically!

---

### Post by Crafty Kisses on 2008-02-23
> **Squish said:**
> I have a Linksys wmp54gx4 wireless card in my computer,  but it does not work.

I dont know what I need to do to make it work.
I am running Ubuntu Studio amd64 7.10
and it is a fresh install, which does not, and can not get internet.

Right now, I am using my ipod to transfer files to it, but It needs wireless on its own... drastically!

Possibly a NDISwrapper.

---

### Post by falkaholic on 2008-02-23
I had a bunch a problem with PPC Ubuntu and a broadcom wireless card. Tried all the common wireless drivers/solutions. Turned out the Restricted Drivers program in Ubuntu found the driver and installed it. Worked great. Sometimes its simple.

---

### Post by dcstar on 2008-02-23
> **Codename said:**
> Possibly a NDISwrapper.

Possibly not, if you use ndiswrapper then you also need a 64bit Windows driver that is ndiswrapper compatible (for x64 systems).

---

### Post by Joe_Strummer on 2008-02-23
First try using the Restricted Drivers Manager.  It would be under System > Administration > Restricted Drivers Manager.

Since you have a 64-bit OS installed, trying to use ndiswrapper to install a driver would be tricky (or at least to my understanding it is), so your best bet for the time being is the Restricted Drivers Manager

---

### Post by Squish on 2008-02-23
Apparently linux drivers do exist at RAlink, I just dont know what chipset to use...
I have heard it is the rt2500 or something

---

