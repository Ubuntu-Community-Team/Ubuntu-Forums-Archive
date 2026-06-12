---
title: "Slow Internet"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by xshady87 on 2006-04-09
I'm fairly new to Ubuntu, and I'm having trouble with my internet connection. I have a cable modem, but am currently running at dial-up speeds. I was told this could be DNS or IPv6, but have not the slightest clue what that means. Any help getting me back on track would be appreciated.

---

### Post by xshady87 on 2006-04-18
any ideas, anybody...

---

### Post by uteck on 2006-04-18
[QUOTE=xshady87]any ideas, anybody...[/QUOTE]
Do you have another computer in the house that is accessing sites faster?  If not, then you may have to call your ISP and talk to them.

---

### Post by Lord_Drakkus on 2006-04-21
I may not be the original poster, but this problem is something very similar to one I've been having...

I have a SIS900 Fast ethernet Card on ETH0 with a 1.5mb DSL connection (aDSL or the like, I honestly don't know, nor do I know how to find out).   It's set up on a Linksys router which shares the internet connection with the computer I'm on now (BTW, the internet works perfectly on this one)...  My ISP Is Charter Communications.

Anyway, when my computer DOES access the internet, it now tends to either go very slow or just sits there and does nothing at all.  I've checked my DNS settings and they're exactly as they should be (192.168.0.1, etc).  In fact, almost exactly the same as this one....

Needless to say, any help would be appreciated.  If any other info is needed it should be pretty easily acquired.

---

### Post by uteck on 2006-04-21
Check the DNS servers listed in /etc/reslove.conf and what is listed in your router.  I tried adding my router to resolve.conf but that seemed to make it worse, so try removing it if it is lised in yours.
Try pining the DNS IPs listed.  I found out that one of the ones I had been using was changed, but the modem was still passing the old info to the router, which was passing it along to the pc's.

---

### Post by xshady87 on 2006-04-21
thanks a lot guys. i tried all of your advice and it's going a lot better.

---

### Post by SuperLou on 2007-02-11
I have an onboard SiS900 LAN but all of my ISP info is set up correctly (the same as my laptop which is also on the same switch).  I have a stable internet connection; it is just VERY slow.  Inside the lan I pull about 1/20 up and down what I get when I boot the same machine into windows.  I hear that there may be an issue on SiS900 cards with the PHY transciever and my dmesg follows:

[17179589.472000] sis900.c: v1.08.09 Sep. 19 2005
[17179589.472000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 209
[17179589.476000] 0000:00:04.0: Unknown PHY transceiver found at address 0.
[17179589.484000] 0000:00:04.0: Using transceiver found at address 0 as default

I have had this problem for a long time.  I didn't know about the PHY transceiver thing until recently as the problem seems more sinister than I origionally thought.  If you have any suggestions please let me know.

Thanks,
Louis

---

### Post by mdscranton84 on 2007-08-03
Hello Fellow Ubuntuinians,
I just wanted to let you guys know that I was having the same problem with the lag/nil activity on Ubuntu through this sis900 lan as well. Removing the router's DNS address from the resolv.conf cleared the problem right up and I couldn't be happier! 
Thanks for the great info!!!
Matt

---

