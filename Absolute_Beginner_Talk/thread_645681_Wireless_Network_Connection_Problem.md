---
title: "Wireless Network Connection Problem"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by cw_yong on 2007-12-20
My system show that my wireless network connection were established at 72% but i am not able to surf the web. Can somebody please help me.THANK YOU

---

### Post by cmnorton on 2007-12-20
Does your wireless router have a web interface, and can you reach that?

---

### Post by cw_yong on 2007-12-20
Yes ...i can reach it....friend

---

### Post by rkd on 2007-12-20
Try opening a terminal and entering:
```
ping 208.67.219.101
```
If you get responses, not timeouts, then your connection to the internet is working at the lowest level.  Maybe just the DNS server address (for getting internet names resolved to their addresses) isn't set up properly.  Tell us the result of the ping and we can tell you what to try next.

---

### Post by cw_yong on 2007-12-20
Error message received were "From 192.168.2.1 icmp_seq=1 Destination Net Unreachable

---

### Post by rkd on 2007-12-20
Is 192.168.2.1 the router's address?  If so, I think that error means the router doesn't have a connection to the outside world.  Do you have another computer that connects through that router and can get to the internet?

If 192.168.2.1 isn't the router's address, do you know what device has that address?

---

### Post by EnergySamus on 2007-12-20
Maybe it is your actual Wi-Fi card. It is possible... I had a problem with mine until I installed firmware. 

Type this abbreviation into the terminal: lspci

Check to see if your Wi-Fi card is there (it will have something to do with ethernet)
If anything says anything about Broadcom, check this out:
  
[URL="https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy"]

Good luck!:)
EnergySamus

---

### Post by EnergySamus on 2007-12-20
Sorry, the web URL was wrong. Here it is in plain English:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

EnergySamus

---

### Post by cw_yong on 2007-12-20
THANK YOU GUYS FOR ALL HELP. But the funny thing was that my system is suddenly ok now. I also noticed that one of the led on my SMC router is now "ON" when it were not last night. The led is having the name of "PPPoe/DSL". I really don't have any idea why maybe you guy can shed some light. MANY THANKS

---

### Post by rkd on 2007-12-20
Withholding evidence! 10 gigabyte penalty!

Seriously, telling us that LED wasn't on would have helped us focus on the real problem.

---

### Post by EnergySamus on 2007-12-20
Yeah, rkd has a point!

I'm glad it now works... So it was the router... Strange8-[

EnergySamus

---

### Post by rkd on 2007-12-20
> **EnergySamus said:**
> So it was the router... Strange8-[

EnergySamus

Not very strange.  That LED being off was saying that the DSL connection was down.  Of course he couldn't surf the web in that case.

---

### Post by EnergySamus on 2007-12-20
I knew that!!! I meant that it was strange that from the start it was the router! 
I know how routers work:lolflag:

Laughs,
EnergySamus

---

