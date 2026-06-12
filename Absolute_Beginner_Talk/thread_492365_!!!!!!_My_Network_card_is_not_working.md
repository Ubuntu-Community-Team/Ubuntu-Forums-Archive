---
title: "!!!!!! My Network card is not working?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by jonnyyoa on 2007-07-04
helppppp............. i switched from pc to ubuntu

 after i installed ubuntu(the latest) i can't get on the internet. i tried pinging but it can't even get to my router. so i'm guessing it has soething to do with my network card. i'm don't know how to "know" what the problem is with my internet. i have my other computers (2 macs)connected to the router and they are all online with good speed. no lag at all. 


i'm really worried

Network card:  Link=>[http://www.amazon.com/D-Link-DWL-520-Wireless-Adapter-802-11b/dp/B000063XJ7]("http://www.amazon.com/D-Link-DWL-520-Wireless-Adapter-802-11b/dp/B000063XJ7")

Pentium 4 (sorry i'm not that go0d with computers), motherboard and stuff (obviously the network card was compatible with the motherboard, because i've been having internet access for more than 3 years.)

Anywho, in the "About hardware" window on my ubuntu, it doesn't seem to know anything about the harware. They are all "Unknown" but the names of the hardwares are there.

i need someone to help out cuz i can't even use beryl :'(  and other stuff.

i really want to use ubuntu to its fullest.

thank you for reading , jon

---

### Post by mlentink on 2007-07-04
Would it be possible for you to get another card? That one seems pretty, ah... old?
I have a Sweex (atheros chipset based) card which I bought for about 11 US$. That worked out of the box...


PS: about Beryl & stuff: please read the stickies. Try to find out exactly what graphics hardware is installed in your machine, because Beryl is still ***beta*** software, not stable, and entirely capable of breaking your system

---

### Post by jonnyyoa on 2007-07-04
okay umm i just found this thingy 

[https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1]("https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1")

is that my network card?

and if it is then am i able to solve the problem without buying a new card?(Cuz i'm not really gonna plan on putting money on that computer.

Btw..... i do not understand the steps in that link at all.......  what's source package? and words like din, uname?? iono i'm very confused.





OH........ SHOOT..... 

sorry i didn't know this wifi card has no ethernet to it...... 

what i'm talking about is my ethernet card that's not working

and i actually don't know what it is.... how do i check with ubuntu?

---

### Post by mlentink on 2007-07-04
You might post the output of 
```
sudo lspci -v
```

---

### Post by lintoon on 2007-07-04
And also post the output of ifconfig.

Open "Terminal" (Applications menu - Accessories) and type in "ifconfig" without the quotes.

---

