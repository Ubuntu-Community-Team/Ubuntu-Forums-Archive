---
title: "Please help me get xircom pcmcia connection to lan going"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Neal McDermott on 2007-02-10
Hi, All,

Thanks for taking the time to read this. I am running Kubuntu 6.10 edgy eft on a Dell Inspiron 3500 laptop. it has a Xircom RealPort Ethernet+Modem 56 pcmcia card (REM56G-10). the computer is connected by this card by ethernet to a lan.

I have only ever used this setup with windows 2000, and all I had to do was  plug in the ethernet cord and I was connected to the internet.

With Kubuntu, it doesn't even seem to recognize that there is a pcmcia card at all. I have been looking around on the internet for a solution, but it is beyond me for now.

Can anyone get me started by a kind of step by step trouble shooting plan to get this card recognized and get connected to the internet.  I don't really know where to start.

Thanks again for your time.

Neal

---

### Post by equability on 2007-03-22
Ciao Neal.

Do you still have this problem or did you find a solution?

---

### Post by Neal McDermott on 2007-03-24
Hi,

Yeah, I got this solved. If you are posting to help out, thank you. If you are posting for a solution, I will tell you what I did.

Basically I boot up the computer and nothing happens with the Pcmica lan card which is connected to the network. I unplug the card, wait a few seconds, and plug it back in again.

Then I go to System Settings > Network Settings. At this point the card is usually recognized as interface eth0. I log into Administrator mode and if the card is disabled, I right click on it and select enable. Then I go over to the "configure interface" button and configure it as DHCP. It works then.

Not the most elegant solution in the world, but it works. It may work for you if you have a similar network setup. Sometimes you have to play around with the order of things, but as long as the interface is enabled and configured as DHCP, it usually works when I unplug and plug back in the ethernet card.

Neal

---

