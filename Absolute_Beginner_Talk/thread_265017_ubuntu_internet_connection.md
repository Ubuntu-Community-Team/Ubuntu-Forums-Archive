---
title: "ubuntu internet connection"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by GonZo1323 on 2006-09-25
i have cable internet works fine for my windows partiation my other ubuntu computer works fine no matter what i do the internet will not connect
i think it has something to do with default gateway device when i change it to eth0-it will not save](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by shashank on 2006-09-25
i know this problem
on windows cmd type ipconfig /all
copy the same (to ubuntu) 
gatway adress and let the dns adress be gateway address
also read about pppoeconfig(may be incorrect! but there is a command to configure pppoe connection!) command in ubuntu

---

### Post by GonZo1323 on 2006-09-25
could u go into a little moer detail im very confused

---

### Post by GonZo1323 on 2006-09-25
bump??

---

### Post by jimminy_kriket on 2006-10-11
A little more explanation on how to do that would be nice.:-k

---

### Post by redbull_monsta on 2006-10-11
Hiya

How do you connect to the cable modem? With the pc directly or is it attached to a router?

---

### Post by guysmiley25 on 2006-10-11
I have a ubuntu machine connected to cable internet on eth1 and connected to the lan on eth0. If you are not using your machine as a router you can ignore the stuff that i'm going to mention. ok so here we go

**Edit:** What I mean is ignore the stuff at the very bottom, this should get your internet working regarless. I just add then rest just incase.

Becasue my ubuntu machine does not have a gui the text editor I will use nano, but if your using xubuntu you can replace with mousepad or kubuntu replace with kwrite or kate, and i'm not sure what ubuntu with gnome uses.

PS < stuff > is stuff you have to put in.

Ok so in the terminal.
```

$ sudo nano /etc/network/interfaces

```

Here is what mine looks like
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address < given by ISP >
netmask 255.255.255.0
gateway < given by ISP >

```

From your windows you can get your IP and gateway. If you only have one eth card just use eth0 and use my details from eth1.

Ok so after you have done that save then exit then
```

$ sudo nano /etc/resolv.conf

```

Then add
```

nameserver < given by ISP >

```

Witch you should also be able to get from your windows as well. It's been along time for me since I used windows but I think in XP there is a icon in the task tray that you can r-click on to get the detail.

**Edit:** Also if you have more than one DNS givin my your ISP you can just append another line eg
```

nameserver < DNS 1 >
nameserver < DNS 2 >

```

Ok so save that then run
```

$ sudo /etc/init.d/networking restart

```

Now hopefully you internet works.

Now if your using you ubuntu machine as a router follow this guide to setup internet sharing

[http://doc.gwos.org/index.php/Share_Internet_Connection](http://doc.gwos.org/index.php/Share_Internet_Connection)

and this one for DHCP

[http://ubuntuguide.org/wiki/Dapper#DHCP_Server](http://ubuntuguide.org/wiki/Dapper#DHCP_Server)

Hope that helps. Any questions just ask. Let me know how you get on.

---

### Post by GonZo1323 on 2006-10-19
i connect through a router

---

### Post by caravel on 2006-10-19
How is your router configured?  Does it use a static IP or is it running the DHCP server?  I use a windows pc as my gateway at present, as I am in neeed of a new router.  The windows pc is using  192.168.0.1 and DHCP is configured.  When I install Ubuntu it's on the net first, time.  In fact the live CD is on the net first time.  Look to your router for clues I would say.

---

### Post by letubenaiah on 2007-06-15
Thanks you so much guysmiley25!  That was very clear and fix my internet connectino problem that I've had for ages!

---

