---
title: "usb 1.1 to 2.0"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-08-27
i know my motherboard has usb 2.0 ports, but do i need a specific driver to use 2.0? i've inlcluded a screenshot of my device manager that makes me think i'm running 1.1.

thanks!

[IMG]http://img.photobucket.com/albums/v330/shanepardue/Screenshot-1.png[/IMG]

---

### Post by Anduu on 2006-08-28
The kernel should automagically detect your usb controllers/devices and adjust accordingly.

---

### Post by Anduu on 2006-08-28
Also scroll down a little farther in the device manager...

---

### Post by jason.b.c on 2006-08-28
How did he get the weather report on his desktop..??

---

### Post by Thirsteh on 2006-08-28
> **jason.b.c said:**
> How did he get the weather report on his desktop..??

gDesklets, prolly.

---

### Post by jason.b.c on 2006-08-28
> **Thirsteh said:**
> gDesklets, prolly.

Where's that at..??

It dosen't exist in the GDesklets homepage...[http://gdesklets.org/?mod=search]("http://gdesklets.org/?mod=search")

---

### Post by shanepardue on 2006-08-28
> **jason.b.c said:**
> Where's that at..??

It dosen't exist in the GDesklets homepage...[http://gdesklets.org/?mod=search]("http://gdesklets.org/?mod=search")

i managed to find the iweather desklet that uses weather.com instead of the outdated yahoo.com desklet. if you want, i can post it for ya

and thanks for the help on the usb issue..i freaked out, ha.

---

### Post by jason.b.c on 2006-08-29
> **shanepardue said:**
> i managed to find the iweather desklet that uses weather.com instead of the outdated yahoo.com desklet. if you want, i can post it for ya

and thanks for the help on the usb issue..i freaked out, ha.

Alright so lets see it...

---

### Post by shanepardue on 2006-08-29
> **jason.b.c said:**
> Alright so lets see it...

[http://par-due.homelinux.org/iWeather.tar.bz2]("http://par-due.homelinux.org/iWeather.tar.bz2")

---

### Post by jdong on 2006-08-29
To answer the original question, Linux will automatically use USB 2.0 if your system supports it. If you look at the hardware manager, you will see at least one "EHCI" controller. Just simply because of the way USB 2.0 was implemented, both 1.1 and 2.0 controllers have to be loaded to use 2.0.

---

### Post by shanepardue on 2006-08-29
thanks jdong!

---

