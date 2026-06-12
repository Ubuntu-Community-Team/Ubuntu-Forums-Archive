---
title: "Getting generic wifi card running"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by grifta67 on 2006-03-26
Hey everyone

I'm new to linux of course, and I'm having trouble getting this wireless card to work.  I know wifi is a trouble spot for linux and I've read through most of the info I could find about it.

The card is a generic CompUSA branded wifi card, with a RealTek chipset, rtl8185.  When doing any kind of search, I'm getting hits for 8180 but not 8185.  I haven't tried using ndiswrapper yet because none of the cards on the list were 8185, they were all 8180.  Will those work?

The driver CD of course only has Windows drivers but the Realtek website offers a linux driver for kernal 2.6.x.  Is this compatable with Ubuntu 5.1?  If so, how in the heck do you install a driver on Linux???  I know that is probably a ridiculous question, but I can't find anything on it.

I hope I'm not missing something obvious, but its late and I'm sleepy and frustrated.  Thanks for any help you can bring!
-Sean

---

### Post by Stewart on 2006-03-27
Try this link. :-k 

[http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=rtl8185](http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=rtl8185)

Ndiswrapper might be the only way to make it work.

Stewart

---

### Post by Titus A Duxass on 2006-03-27
Stewart - "Try this link.  

http://www.realtek.com.tw/downloads/...eyword=rtl8185"

I think you'll find he has already been there.

Grifta,
Do a search for rtl8180 and I think you will find a guide for that chipset, you could try it with your chipset.

Ndiswrapper will also probably work, it does with my rtl8180 card.

I have never been able to follow the RealTek linux how to, let us know if you have any success.

[http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/) this a link to the sourceforge.net page but you have to be a rocket scientist to understand it.

---

### Post by grifta67 on 2006-03-27
Well I think I've made progress but no success yet.  I used the most recent XP drivers for my card with ndiswrapper to get Ubuntu to recognize the wifi card.  Its listed now in the Network window and when I run iwconfig.  When configuring the wifi card, it sees my network in the dropdown menu.  After that though, I get nothing.

When I run "ifup wlan0" it trips up at the DHCPDISCOVER command.  It just keeps getting no response after trying at every interval.  I'm confident that it is not a problem with my router or network, as right now I'm posting from my other PC running Ubuntu.  I ran the "ifup wlan0" on my machine and it worked fine.  I did try restarting the router just in case with no results.

Any ideas?

Thanks
-Sean

---

### Post by Titus A Duxass on 2006-03-28
Have you changed your /etc/network/interfaces file?
Have you added ndiswrapper to /etc/modules

Try switching off the pc (don't unplug), remove card, restart, switch off (don't unplug), replace card, restart.

I have this problem with my 8180 card, maybe you have similar problems.

---

