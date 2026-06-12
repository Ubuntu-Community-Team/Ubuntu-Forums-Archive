---
title: "refresh rate problems"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2006-12-21
Recently my GUI has been acting up, having extremely slow scrolling speed when I e.g. try to view documents.  I've been messing around with X server recently to have it work with my graphics card (which is a whole other problem), and I suspect that I accidentally changed a refresh rate or something.  Does anyone know what I'm talking about?  

Thanks for the help.

---

### Post by riven0 on 2006-12-21
> **oscar78 said:**
> Recently my GUI has been acting up, having extremely slow scrolling speed when I e.g. try to view documents.  I've been messing around with X server recently to have it work with my graphics card (which is a whole other problem), and I suspect that I accidentally changed a refresh rate or something.  Does anyone know what I'm talking about?  

Thanks for the help.

The easiest way to fix this is to do a **sudo dpkg-reconfigure xserver-xorg** and reboot the comp.

---

### Post by oscar78 on 2006-12-21
yes, that's what I have been trying to work with for the past couple hours.  Would you know what parameters I would have to change to fix my problem?

---

### Post by riven0 on 2006-12-21
> **oscar78 said:**
> yes, that's what I have been trying to work with for the past couple hours.  Would you know what parameters I would have to change to fix my problem?

Well, what is the make and version of your monitor? You probably don't have the booklet that came with it, but perhaps we can find the refresh rate values on the net.

---

