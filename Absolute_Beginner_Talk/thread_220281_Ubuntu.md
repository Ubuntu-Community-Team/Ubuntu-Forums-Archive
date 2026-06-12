---
title: "Ubuntu"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Gordon Barnes on 2006-07-21
Can anyone help, please?  

I configured Ubuntu to run on a 19" CRT monitor but when I connect a TFT 15" monitor I receive a message that says: "Input sigmal out of range".  

If I run Ubuntu from a CD it runs OK.

Any ideas, please?

---

### Post by wieman01 on 2006-07-21
It's the resolution and the refresh rate, mate. It's likely plugging a toaster into a high-voltage power supply. 

The Live CD can change resolution and refresh rate according to the device that you have connected. An configured system cannot do that, same thing under Windows.

---

### Post by zhoux on 2006-07-21
run withink terminal:

```
dpkg-reconfigure xserver-xorg
```, 

and when it asks you about your monitor settings, choose the approriate one

---

### Post by Gordon Barnes on 2006-07-22
> **zhoux said:**
> run withink terminal:

```
dpkg-reconfigure xserver-xorg
```, 

and when it asks you about your monitor settings, choose the approriate one


Many thanks, I now have a working monitor.

---

### Post by Gordon Barnes on 2006-07-22
Many thanks.  I now have a working monitor.

---

### Post by Dommel on 2006-07-22
> **wieman01 said:**
> It's the resolution and the refresh rate, mate. It's likely plugging a toaster into a high-voltage power supply. 

The Live CD can change resolution and refresh rate according to the device that you have connected. An configured system cannot do that, same thing under Windows.

Erm, Windows will just detect different monitor and resize the resolution according to that. One of my pet peeves of linux for years, why do i have to go edit xorg.conf (or xfree86 in the past) just cause I connected a different monitor.

---

### Post by wieman01 on 2006-07-22
> **Dommel said:**
> Erm, Windows will just detect different monitor and resize the resolution according to that. One of my pet peeves of linux for years, why do i have to go edit xorg.conf (or xfree86 in the past) just cause I connected a different monitor.

Ah... you are right. It has been a while... Agree, annoying thing in Linux. Glad to hear this has been resolved.

---

### Post by Frank Golden on 2006-07-22
Just a subtle reminder that we ain't in Kansas anymore, Toto.:p
Pay no attention to the little man behind the curtain.

---

