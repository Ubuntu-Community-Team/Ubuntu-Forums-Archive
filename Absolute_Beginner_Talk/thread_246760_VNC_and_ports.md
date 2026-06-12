---
title: "VNC and ports"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by nowadays who knows on 2006-08-29
OK here is the situation and my question from work i need to vnc to home with 2 pc's . One is xp, and the other is ubuntu/xp. Through my home linksys router i use a nonstandard port to forward to the ubuntu/xp box. when in xp i know how and have told my flavor Ultra vnc to use 5910 instead of 5900 for ports and I can then vnc into the ubuntu/xp box or other xp box depending on adding :5900 or :5910 to the addres. 

My question is How in UBUNTU do I get vnc(any flavor) to respond to a port besides defaults????   ANYONE got any clues????:confused: ](*,)

---

### Post by atomkarinca on 2006-08-29
first of all, you should listen the port you want:

vncserver -rfbport port-number

then you should connect typing:

vncviewer serverip:portnumber (or the graphical way)

ps: if you want to connect via a port less than 100 you must substract that from 5900. for instance if you want to connect via port 80:

vncviewer serverip:-5820

---

### Post by nowadays who knows on 2006-08-30
Hmm Sounds interesting ill give it a try and get back with you thans for the tip.:-k :)

---

