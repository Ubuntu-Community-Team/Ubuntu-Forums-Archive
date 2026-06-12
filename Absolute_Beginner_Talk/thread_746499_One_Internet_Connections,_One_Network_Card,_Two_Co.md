---
title: "One Internet Connections, One Network Card, Two Computers"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-04-05
Assume computer A has one wireless network card, with one ethernet port as well. Would it be possible to connect computer B to the network card on computer A and share the wireless connection being fed from a wireless router? If so, how? And would it be anymore difficult if computer A was a windows machine and computer B was an ubuntu machine?

---

### Post by mikeyphi on 2008-04-05
An interesting thought but (I think) not possible. You would need a network card attached to computer B - without (at the same time) being attached to computer A.

Does compute B have a USB port? for a wireless stick.

---

### Post by ghost_ryder35 on 2008-04-05
If the wireless card and wired connection are diffrent cards then it is possible. Doing it with a Windows machine I am sure will throw a curve ball in the mix. For starters your going to need a crossover cable, not the typical cable you pick up from best buy (although they have them). 
This should point you in the right direction
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
[http://www.debuntu.org/iptables-how-to-share-your-internet-connection](http://www.debuntu.org/iptables-how-to-share-your-internet-connection)

---

### Post by Sinkingships7 on 2008-04-05
computer B does have a network card. Onboard ethernet. For clarification, my computer is computer B and my friends computer is computer A. i'm going to his house to spend the night tonight and i wanted to bring my computer over and share the internet connection. However, I do not have a wireless card, just onboard ethernet. So, knowing that, do you think it is possible to connect my computer to his wireless card via a normal cat5 cable, and share the connection coming to his wireless card from the wireless router downstairs?

---

### Post by mike23 on 2008-04-05
I think there is some place in windows that has an option called "share this internet connection"
I personally haven't tried this out nor i know what this does! just mentioning maybe it helps.... :)

---

### Post by Sinkingships7 on 2008-04-05
> **ghost_ryder35 said:**
> If the wireless card and wired connection are diffrent cards then it is possible. Doing it with a Windows machine I am sure will throw a curve ball in the mix. For starters your going to need a crossover cable, not the typical cable you pick up from best buy (although they have them).  
This should point you in the right direction
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

How convenient. I just so happened to have made a crossover cable the other day, so I do have one that I made myself, tested working. What would I need to do?

---

### Post by ghost_ryder35 on 2008-04-05
> **Sinkingships7 said:**
> How convenient. I just so happened to have made a crossover cable the other day, so I do have one that I made myself, tested working. What would I need to do?
check out the links I posted, I dont have specifics for your config, so I posted some how toos that you will have to "adapt" for your configuration

---

### Post by ugm6hr on 2008-04-05
This should be very easy.

Connect as expected:
Computer B LAN card - crossover cable - Computer A Lan card

Computer B (Ubuntu) setup - DHCP on (in Network settings, or use roaming mode).

Computer A (Windows) setup - assuming XP - is very easy to share an internet connection from (easier than Ubuntu).  I haven't had to do this in Windows for a few years - but this looks familiar (just follow the "host computer" advice): [http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)

---

### Post by Sinkingships7 on 2008-04-05
> **ugm6hr said:**
> This should be very easy.

Connect as expected:
Computer B LAN card - crossover cable - Computer A Lan card

Computer B (Ubuntu) setup - DHCP on (in Network settings, or use roaming mode).

Computer A (Windows) setup - assuming XP - is very easy to share an internet connection from (easier than Ubuntu).  I haven't had to do this in Windows for a few years - but this looks familiar (just follow the "host computer" advice): [http://support.microsoft.com/kb/306126](http://support.microsoft.com/kb/306126)


it should be as simple as that?

I won't have to mess with anything on my ubuntu PC, right? It should just work from the XP pc?

---

### Post by Sinkingships7 on 2008-04-05
bump

---

### Post by ugm6hr on 2008-04-06
> **Sinkingships7 said:**
> it should be as simple as that?

I won't have to mess with anything on my ubuntu PC, right? It should just work from the XP pc?

I figured this was a question to other users to confirm my info.

But since no one else has replied.... Yes.

I have shared a wifi signal via crossover Ubuntu-Xubuntu recently, and computer B does not need any settings (apart from DHCP), since it "sees" computer A as a router (it doesn't care that it is a computer at all).

I have previously shared a dial-up signal via XP (which shows how long ago I did it!), which was just as the link I gave (from memory).  In fact, I worked it out by experimentation.  Computer A doesn't care whether B is Ubuntu or XP - it merely acts as a router with DHCP.

---

