---
title: "Can I ??"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by Titus A Duxass on 2006-02-07
I have a wireless router with one hard wire connection to my main pc connected to the on-board ethernet card. 

I would like to have another hard wire connection to the net.

Can I put another ethernet card in the main pc and then connect to it as and when required?

Can I do all this without a) losing the wireless functionality and b) without buying more hardware (routers and switches, I already have the ethernet card)?

Any advice will be appreciated.

Thanks in advance.
Titus

---

### Post by rmjokers on 2006-02-07
So, you want to have 2 ethernet cards with wired connections to your wireless router?  Is there any particular reason you want to set up the network this way?

---

### Post by mips on 2006-02-07
Why would you want to do this ?

You cannot have two network interface on one device within the **same** network, TCP/IP design does not cater for this.

The only way to have multiple interfaces in the same network is to use a tecnique called NIC-bonding. You basically bond multiple physical interface together via a Virtual interface that gets the TCP/IP config. Multiple interfaces then appear as one.

---

### Post by Titus A Duxass on 2006-02-07
The reason I want to do this is as follows:

I have another pc and need it on line to install software, I am running everything from the command line.

I want to be able to search using my other pc at the same time, I was hoping that I could set this up.

It sounds possible but I think you have to be a rocket sceintist to be sucessful.

I think what I am trying to do is set up the main pc as a router but retain the normal pc functions.

I am I making myself clear or am a doing this in Germish?

---

### Post by Iowan on 2006-02-07
IMHO, you should be able to set up the one PC as a router (still use it as a pc) and establish the wireless and other pc on subnets.  As to how it's done... :-k

---

### Post by mips on 2006-02-07
Titus,

That you can do with no problem. I think you explained yourself incorrectly.

Simply plug the second PC into your router and bobs your uncle, no rocket scinece required.

If you want you can also connect it to you current PC with minimal effort. Look at Firestarter Internet connection sharing, a breeze.

---

