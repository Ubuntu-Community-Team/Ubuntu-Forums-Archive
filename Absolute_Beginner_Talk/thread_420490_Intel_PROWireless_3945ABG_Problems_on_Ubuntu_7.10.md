---
title: "Intel PRO/Wireless 3945ABG Problems on Ubuntu 7.10"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Jolzath on 2007-04-23
I am new to Linux, and as usual the new guy has a problem for you. I have a Acer Aspire 5601 with a Intel PRO/Wireless 3945ABG network connection (dual-band tri-mode 802.11a/b/g) Wi-Fi CERTIFIED solution, supporting Acer SignalUp wireless technology. I install Ubuntu 7.04 (Feisty Dawn) which works wonders, till I find out that I cannot connect to the internet through wireless. The driver is filed as a restricted drive. I have searched and searched for an answer, but most of them were talking about Ubuntu 6.10. Perhaps with your knowledge of Ubuntu and Unix language. To help me fix this problem. Thank you.

---

### Post by annda on 2007-04-23
have you tried enabling the driver in system > administration > restricted drivers manager and rebooting? that should help.

---

### Post by Jolzath on 2007-04-23
> **annda said:**
> have you tried enabling the driver in system > administration > restricted drivers manager and rebooting? that should help.

It has always been enabled.

---

### Post by annda on 2007-04-23
what can you do from the network applet in the panel? can you not configure your connection? where exactly is the problem?

---

### Post by Jolzath on 2007-04-23
> **annda said:**
> what can you do from the network applet in the panel? can you not configure your connection? where exactly is the problem?

 It doesn't even show up that I have wireless. Wired and Modem connections are the only ones I can see in Network Settings. Nothing in Location, see nothing to add a connection, or configure...

---

### Post by annda on 2007-04-23
sorry for the stupid question, but is your wireless switch on?

also, can you see the intel wireless interface when you type this in the terminal?

```
sudo lshw -C network
```

---

### Post by Jolzath on 2007-04-23
> **annda said:**
> sorry for the stupid question, but is your wireless switch on?

also, can you see the intel wireless interface when you type this in the terminal?

```
sudo lshw -C network
```

:lolflag: I feel so dumb XD I was so fixated on the problem I forgot something so basic, Thats what I get for being on windows so much I never had to use the switch, I made it a quick keyboard press..thank you for that stupid question, it made me recheck it. Back when I had Windows on this machine, I got pissed one day, and made a small dent that makes the switch get stuck and makes the Bus card button a little hard to push...but all in all, it just proves the stupid questions and the linux newbs go together...Thank you again, by the way what source of information do you find best to find out about the Unix language, and the Ubuntu system as a whole?

---

