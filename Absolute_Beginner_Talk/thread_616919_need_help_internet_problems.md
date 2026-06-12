---
title: "need help internet problems"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by moondoggy17 on 2007-11-18
ok i will try to explain this as best as i can.
 i have a compaq Presario it has a ASUS P4GV-LA mother board, 256 MB DDR PC 2700 ram.
all the components like video cards and network cards are built onto the mother board.
in the device manger in windows xp  calls my network card Realtek RTL8139/810x Family Fast Ethernet NIC

I have RCA cable Modem connected to a Linksys router connected to my computer

now i'm useing Ubuntu 7.10 dual boot with windows xp

now whaen i boot up to windows i can look at my router  and it can tel that the computer is on by lighting up lamp num. 1 under ethernet, but when i boot into ubuntu it doesn't show up on my router at all (it doesn't show up on my modem when its directly connected)


here is a screen shot of Network tools on ubuntu 
[IMG]http://i105.photobucket.com/albums/m201/goemon17/Screenshot-Devices-NetworkTools.png[/IMG]

it also shows another network interface
[IMG]http://i105.photobucket.com/albums/m201/goemon17/Screenshot-Devices-NetworkTools2.png[/IMG]

but when you try to configure it i get this msg
[IMG]http://i105.photobucket.com/albums/m201/goemon17/Screenshot-network-admin.png[/IMG]

so if any one knows what i should do please help me

---

### Post by Pumalite on 2007-11-18
Post:
sudo lshw -C network

---

### Post by fourscore on 2007-11-18
There is an issue with Realtek Ethernet card when dual booting with Windows and Linux.       Pls  refer to the flwg link - [http://ubuntuforums.org/showthread.php?p=3446114](http://ubuntuforums.org/showthread.php?p=3446114)

---

### Post by moondoggy17 on 2007-11-18
> **Pumalite said:**
> Post:
sudo lshw -C network

explain
should i typ that in the Terminal window?
:confused:

---

### Post by oilchangeguy on 2007-11-18
> **moondoggy17 said:**
> explain
should i typ that in the Terminal window?
:confused:

this is to easy. just type what the poster told you to type.

---

### Post by Pumalite on 2007-11-18
> **moondoggy17 said:**
> explain
should i typ that in the Terminal window?
:confused:
Yes.

---

### Post by moondoggy17 on 2007-11-18
> **Pumalite said:**
> Post:
sudo lshw -C network

all i got from that was this
[IMG]http://i105.photobucket.com/albums/m201/goemon17/Screenshot-moonpimp.png[/IMG]


and 

> **fourscore said:**
> There is an issue with Realtek Ethernet card when dual booting with Windows and Linux.       Pls  refer to the flwg link - [http://ubuntuforums.org/showthread.php?p=3446114](http://ubuntuforums.org/showthread.php?p=3446114)

i did what the link said and it work thank you very much for your help
:guitar:

---

### Post by Pumalite on 2007-11-18
Glad you got it working! Bookmarked the link too.

---

