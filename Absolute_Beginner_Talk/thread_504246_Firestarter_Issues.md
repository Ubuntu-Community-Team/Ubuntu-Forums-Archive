---
title: "Firestarter Issues"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by GreenLungz on 2007-07-18
Alright heres another bit of help, when I try to configure Firestarter I have no clue really how to determine what kind of connection I have, so when I do get it configured how I'd think it should be(?) it gives me this error 

> the device eth0 is not ready
please check your network settings....so on and so forth. 

I'm getting my internet fix off of an AirPort and I've heard along the way that enabling the firewall is not really all that important if running though a wireless hub but something tells me thats being a little too optimistic about things, I've gotten screwed by viruses often enough.

Any help?



**Edit**

Anyone else notice that the Ubuntu logo looks a lot like the rotary one?

---

### Post by djchandler on 2007-07-18
> **GreenLungz said:**
> Alright heres another bit of help, when I try to configure Firestarter I have no clue really how to determine what kind of connection I have, so when I do get it configured how I'd think it should be(?) it gives me this error 



I'm getting my internet fix off of an AirPort and I've heard along the way that enabling the firewall is not really all that important if running though a wireless hub but something tells me thats being a little too optimistic about things, I've gotten screwed by viruses often enough.

Any help?

Firestarter is not the actual firewall; it's the GUI frontend for configuring your firewall. Unless you are having problems like you think someone has hacked in, or that somebody wardriving is getting on your network (this is why I don't trust wireless networking), then I wouldn't play around with firestarter. The main reason for the average user running firestarter is to *open* ports.

DJ

---

### Post by dpar on 2007-07-18
You don't really have to worry about viruses with Linux.

---

### Post by GreenLungz on 2007-07-18
> **dpar said:**
> You don't really have to worry about viruses with Linux.

Music to my ears:-({|=

---

### Post by 5-HT on 2007-07-19
> **GreenLungz said:**
> 

Any help?

Under the preferences there is an option to choose the networking device. Run 'ifconfig -a' to find out which device is your wireless, and select that device in firestarter's preferences.

cheers,

---

