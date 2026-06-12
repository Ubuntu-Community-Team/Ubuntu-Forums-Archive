---
title: "Linksys Wireless 54mbps PCI Adapter Card Linux Drivers"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by tc3racer on 2006-07-30
can any one tell me if there is any Linksys Wireless 54mbps PCI Adapter Card Linux Drivers or is there a way to install windows drivers on linux 

see: [http://ubuntuforums.org/showthread.php?t=225175](http://ubuntuforums.org/showthread.php?t=225175)

otherwise iam gonna be stuffed please help

---

### Post by dmizer on 2006-07-30
it would help to know exactly which one.  there are several kinds.  i have created a howto for the wpc54g ver 2 (link in my sig) but it's a pcmcia card.  there are other howto's with linksys cards using broadcomm chipsets.

most of the howto's i've seen do not use linux default drivers.  i know the card i use can work with linux drivers but they are flaky at best.  if you are using a broadcomm chipset, your best bet will be to load windows drivers via ndiswrapper, but i'm not sure if that's possible with pci cards.

---

### Post by tc3racer on 2006-07-30
the card is a Linksys Wireless 54mbps PCI Adapter Card  model :WMP54G

---

### Post by dmizer on 2006-07-31
reports are that this will work with ndiswrapper and the windows drivers.  give it a shot and post if you run into a snag.

---

### Post by tc3racer on 2006-08-02
thanks i will give it a go and i will keep ya posted if i run into any probs;)

---

### Post by tc3racer on 2006-08-07
Im still not sure about the Linksys Wireless 54mbps PCI Adapter Card has anyone definatly managed to get it to work

---

