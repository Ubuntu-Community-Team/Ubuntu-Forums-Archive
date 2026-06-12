---
title: "Vista systems hogging bandwidth."
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2008-03-14
I have two new laptops running Vista. Before they arrived, my DSL was about as fast as my cable used to be. 

Once these two showed up, my ubuntu box is getting the speed I used to get on a bad dial-up... 

Does anyone know how to either give my system priority, or to do something on the Vista boxes that will speed us up?

Thanks

EDIT: Oh yeah... It's a wireless network for all of them. The laptops replaced desktops with XP that were wireless as well, but with XP, they didn't slow up the network...

---

### Post by supermelon928 on 2008-03-14
Well before I can offer any words, may I ask why you run Vista on two computers?

---

### Post by SOULRiDER on 2008-03-14
Im not sure doing load balancing is that simple. You could limit the Vistas machines speeds on each laptop by using a program like NetLimiter akthough its not the best solution of all...

---

### Post by jrusso2 on 2008-03-14
Vista in and off itself should not be hogging bandwidth. However a nic thats generating errors could slow down a segment.

I would look into that possibility.

Unless your running torrents or streaming media on the other pc's?  What are they doing?  Some home routers can get overwhelmed if you put too much traffic on them.

---

### Post by Papa-san on 2008-03-14
Vista is on them because my wife insisted they have it for our daughters. I'm setting them up as dual boot with Ubuntu, but am currently dead in the water due to a wireless issue with them. 

The slow-down happens when they are both in a java chat and might be looking at you-tube. They aren't downloading anything.  And neither am I. It just gets S_L_O_W...

The worst part is that I have a third one of these things set to arrive on the 25th... :(
(also infected with the Vista virus.)

---

### Post by canthus13 on 2008-03-14
Youtube sucks up bandwidth, and windows updates also suck up bandwidth, but this shouldn't be a constant issue.

Depending on your router, you may be able adjust the QoS settings to keep the laptops from sucking up all of your bandwidth.

---

### Post by Papa-san on 2008-03-15
When I have my laptop and a new one running Ubuntu, there is a significant difference, and once I get the wireless issue worked out on the new machines, I'll try running all three and see how well that works. 

I do know that Vista, on its own, is really, really slow: I find myself re-clicking things because I assume the double-click didn't register, but it's just lagging... This happens on a 2.7 Gh dual core processor with 2 Gh of ram... I run the Ubuntu partition on the new one I have it installed on, and it is lightning fast... 

I just cannot wait until I can convince my wife that Linux is a better way than anything Windows has to offer... Unfortunately, I tried to set her desktop up as a dual boot before I knew what I was doing, and made it a very bad experience for her... 

So... as far as the QoS settings, are there any suggested parameters? I've never messed with them, but the router interface shows that I can adjust them (see screenshot, below). First and foremost, I don't want to screw them up. ](*,)

---

### Post by canthus13 on 2008-03-15
Wow... I'm not really sure with yours.  I run DD-WRT on my router, and the QOS settings allow you to pick a MAC address or Ethernet port and assign it a priority.  I'd check the manufacturer's website for some help with the QOS settings for your router.

---

### Post by Mithrilhall on 2008-03-18
You could also setup a packet shaper ([www.mastershaper.org](www.mastershaper.org)).

---

