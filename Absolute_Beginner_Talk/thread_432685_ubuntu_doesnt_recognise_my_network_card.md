---
title: "ubuntu doesnt recognise my network card?"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-05-04
ubuntu doesnt recognise my network card, and i dont have any drivers for ethernet.
All I know is that I have 10Mbit LAN..

When I had windows installed, network worked fine (I have a router, so I dont have to configure nothing).

What to do?

---

### Post by Scorpuk on 2007-05-04
Can you post the reults of lspci?


In a terminal window type:


```
lspci
```


This shoudl list all PCI atatched devices. From there it shoudl list the manufacturer and model of your network card.

---

### Post by baysl on 2007-05-04
I dont have ubuntu installed yet.

During the installation I get information that he doesnt find any ethernet devices.

---

### Post by h0ax on 2007-05-04
What kind of ethernet card is it?
Computer?  Is it a Dell ?

---

### Post by baysl on 2007-05-04
Computer is pentium II MMX 300MHz, card is standard 10Mbit

---

### Post by KCormier on 2007-05-04
We either need the model number of the card or if it's integrated, the model number of the motherboard

---

### Post by baysl on 2007-05-04
3COM EtherLink III is the card and its not integrated on mainboard...

---

### Post by jargoman on 2007-05-04
I've been looking into this. I don't see why your cards not supported. is it possible to get the exact chipset of your card or the model number of your computer 
ie

3Com EtherLink III 3c509 TPO ISA
 
or 

in my case of laptop
hp pavilion dv5216ca 

One way of getting the chipset of your ethernet card would be to open up your comuter and literally look at the chip for a model number. Sometimes it's on a sticker.

perhaps the drivers for your card are restricted, meaning ubuntu doesn't support them but you may be able to add them yourself.

---

### Post by jargoman on 2007-05-04
can't you just run ubuntu live from the cd without installing and post

$ lspci

noting that you may have to transcribe it by hand you might wanna post

$ lspci | grep EtherLink

---

