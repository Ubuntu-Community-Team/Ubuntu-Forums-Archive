---
title: "having trouble setting up my internet"
date: 2005-07-15
forum: Absolute Beginner Talk
---

### Post by porsher_puddles on 2005-07-15
Ok i'm totally new the linux, i'm pretty used to windows but sick of all the viruses etc. i got a copy of ubuntu free with a pc mag awhile back, i have been meaning to have a play with it, so i put together an old pc, 667 celeron on a hp invent motherboard, two physical hard drives one with windows ME on the other to try ubuntu.
The install went fine it seemed very easy and user friendly, i do however get a fail message when it boots, this says ROR  temp fail in name resolution, i do not know if this is a big problem or a driver missing or the such like. Everything seems to be working as far as i can tell, i have sound, devices such as cd rom etc work ok, my modem is listed in the devices section, although i don't know how you query it to check. my modem is an internal pci type.
my problem is i can't seem to work out how to set up my dial up internet., in windoes its just a case of typing in your dial up number and user name and password, and your away, i can't find anyware to do this.
i am told i am probably using ubuntu warty if thats a help, but i don't know how to check which version i have.
any help would be appreciated
ty in adavance

---

### Post by pchachte on 2005-07-15
Nearly all pci modems are 'winmodems.'  Some of them can be made to work on Linux (others cannot).  Most Linux enthusiasts will tell you that they're lousy modems and that you are better off with a cheap external modem.  I have had some success getting winmodems to work in the past.

check these web pages which might be able to help you figure out whether or not this is your problem.

[https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)

[http://www.linmodems.org/](http://www.linmodems.org/)

good luck!

---

### Post by evilghost on 2005-07-15
I feel sorry for you having to use dialup.  If you trust me enough to provide your mailing adress I will gladly send you a 3COM v.90 External FaxModem.  It's got the TI DSP so you should actually see some great performance out of it.  I'll also send you the DB9 to DB25 cable and the DC9V adapter.  From there, setting it up should be a piece of cake and you'll get to see the pretty flashing lights.  I would ask that you pay shipping, and would only charge you the real rate, I'm not out to make a profit.

---

### Post by porsher_puddles on 2005-07-15
ty evilghost for your kind offer, but i have found an external modem i had forgotton about its a web excel 56k. i have plugged it in and powered it up, windows would of detected the device and asked for drivers etc.
what do i have to do with ubuntu ? i can't see it listed in devices, where can i get a driver or a least a standard driver that has basic functions

---

### Post by evilghost on 2005-07-15
I think it gets installed as /dev/modem, or /dev/ttyS0, where 0 = Com1, 1 = Com2, 2 = Com3, 3 = Com4.

It's been so long since I've played with a modem in Linux...I don't think drivers are necessary since it will use serial I/O.

See [http://www.ubuntuguide.org/#gnome-ppp](http://www.ubuntuguide.org/#gnome-ppp) and [http://www.ubuntuguide.org/#configuredialupconnections](http://www.ubuntuguide.org/#configuredialupconnections)

pppconfig looks like your answer, and gnome-ppp is probably a front-end GUI to that.

---

### Post by porsher_puddles on 2005-07-16
ok so now what do i do to set up my internet, what are the steps? as i said in windows i type in my dial up nimber and user name and password and its away. what do i do in ubuntu warty?

---

### Post by evilghost on 2005-07-16
See my edit on my most last post.... :)

---

### Post by porsher_puddles on 2005-07-16
ah making abit of progress here i see how it works now, i haven't quite worked out exactly what to type in all the boxes yet, i get does not exist message so i'm still doing something wrong, but i'm on my way i think

---

### Post by evilghost on 2005-07-16
I hope I've got you moving in the right direction, I'd like to help more but I've not living in the world of Dial-UP  ;-)

---

### Post by porsher_puddles on 2005-07-16
well you have certainly got me moving in the right direction, its obviously different from windows which i would set up in 2 seconds, but i really like the look of ubuntu and it  is running amazingly well considering its straight out of the box, once i get the dial up going i will set about updating things but i will cross that when i get to it, ty so much for your help

---

