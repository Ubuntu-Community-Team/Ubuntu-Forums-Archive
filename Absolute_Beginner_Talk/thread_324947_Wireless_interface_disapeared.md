---
title: "Wireless interface disapeared?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by Ronfar on 2006-12-24
I've been running Ubuntu Dapperdrake on my desktop for about 4 months and I liked it so much that I decided to purchase a System 76 laptop. So I got it about two days ago and everything has been working great so far, however yesterday I turned my laptop off for the night and to my suprise this morning my wireless interface wasn't showing up. 

So I played around for it and went into /etc/network/interfaces and saw that it was no longer in there, well I added it back but nothing was resolved from that. I've also tried to reinstall the drivers that system 76 sent me with no success. So my question is do you think it's a hardware problem or did something mess up and I need to reconfigure something. The laptop is running the most recent verison of Ubuntu Edgy and the wireless device is a Intel PRO/Wireless 3945AB, It also shows up as Eth2.

I really apperciate anyone taking the time to help out!

---

### Post by orb9220 on 2006-12-24
Did you go to the system76 site and ask them since it is their system and might know paticular issues?

If it was network-manger that you were using before? Then in the /etc/network/interfaces file try having only the auto lo line at the beginning and everthing else commented out with a # in front of every entry. Then reboot.

Hope this helped.

---

### Post by Ronfar on 2006-12-24
Hey thanks for the reply. I tired what you said and was unsuccessful, I also found a few old threads where people have had similar problems with this specific wireless card. In one of those threads it mentioned that the linux restricted modules weren't updated or installed. Well I did that with no success, hopefully someone might have an idea to try out for this problem. thanks

---

