---
title: "is Ubuntu for Toshiba Satellite M30 laptop?"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by babyboss on 2006-03-31
I love ubuntu on my desktop, now I also want it to be installed on my laptop. However, I had bad experience with installing debian on my laptop. Therefore, I am here to ask if Ubuntu fully supports my Toshiba Satellite M30 laptop?

---

### Post by frodon on 2006-03-31
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteM30X-162?](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteM30X-162?)
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteProM30-690?](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteProM30-690?)

---

### Post by babyboss on 2006-03-31
I have seen them. Do you have a M30 laptop? Do you install Ubuntu on it. Does it run smoothly?

---

### Post by frodon on 2006-03-31
By the way, if you don't want to install ubuntu if you're not sure it will work perfectly, i advice you to play with the liveCD, you will see quickly if it works smoothly.
In addition i'm sure you will find users with the same laptop here. 
[http://ubuntuforums.org/showthread.php?t=88710](http://ubuntuforums.org/showthread.php?t=88710)

---

### Post by nab on 2006-04-10
Hi,

I'm using a m30x-165 with breezy on a daily basis. Most things I want to use, are working. Things i couldn't get to work are modem, sd-card-reader, multimedia keys, wlan with wpa (wep is working without problems). But I'm just some DAU with little linux expertise.ve to use unsupported hardware

Main thing using ubuntu-live-cd is starting it with the right boot parameters:

hw-detect/start_pcmcia=false noapic nolapic acpi=off vga=790

was working for me with breezy

Installing ubuntu on my hard disk I had to exclude some memory to get pcimcia and tweak some other things, searching this forum will help you to get most things working :-)

Now I'm pretty content with my linux box and start windows only for some simulation tools and if I have to use some unsupported hardware.

Hope this helps :-)
Niko

---

