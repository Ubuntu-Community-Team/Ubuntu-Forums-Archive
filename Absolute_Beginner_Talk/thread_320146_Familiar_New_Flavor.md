---
title: "Familiar New Flavor"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by jpoRS on 2006-12-16
Hey,

I am running Edgy on a hp Pavillion dv4000 laptop.  I am home from school for Christmas break, and have found that I can't connect to the wireless here in my house.  I think we have a WEP network, so it isn't the WPA issue.  The wireless worked fine at school, both on the open university network and the closed network me and my roommate have.  I would try the numerous fixes I have found here and in other places, but I can't get a wired connection because my family uses Verizon broadband, and they don't support Linux.  So if anyone knows a way i can get around the verizon block or fix the wireless problem using only what is on my computer, I would be very thankful.

jim

---

### Post by patrick.dylan on 2006-12-16
Here are a few things to try, although not really ubuntu related:

- Check the wireless router settings make sure that it's not filtering MAC addresses or otherwise preventing your laptop from connecting. Can you see the network from your laptop? 

- "Linux support" by Verizon shouldn't matter. If they have a home network with broadband, you can get on that network and get an internet connection. try enabling your ethernet port and plugging into the router directly to see if you can get on the network that way.

---

### Post by jpoRS on 2006-12-17
Something screwy is up with this modem.  I had trouble with it when I was still using XP, and now this.  I can't get to the router settings in any way I am familiar with, have tried several ways to fix it from this computer (my parents XP Desktop).  I am pretty clueless when it comes to Windows.  Anyone know how to modify a Westell 327w?

I also tried the direct wired connection. It connected but told me that since Verizon didn't support Linux it wouldn't go through.

thanks
jim

---

### Post by seijuro on 2006-12-17
I had verizon dsl never had a problem with running linux with it. If you have another router you can set the verizon modem up for bridge mode and have the better router handle the connection with verizon westel bl0wz. I set mine to bridge mode and let my netgear handle everything. Check with google see if you can find a manual for the modem it should tell you in there how to set bridge mode if you are locked out of the modem you can try resetting it to factory defaults. You'll need your username and pass to connect to veriozon tho. I'd give you the info on how I did it but I don't have the same modem so I don't know if the directions would apply or not.

---

### Post by jpoRS on 2006-12-17
I followed the instructions I found in the Westell manual, Firfox and Internet Explorer both told me that the addresses I was requesting didn't exist.  Am I safe assuming that the problem lies in the router, as I have heard that this router is useless.  I guess it is time to look for a real one.  Any suggestions for a good router?

jim

---

### Post by jimrz on 2006-12-17
> **jpoRS said:**
> I followed the instructions I found in the Westell manual, Firfox and Internet Explorer both told me that the addresses I was requesting didn't exist.  Am I safe assuming that the problem lies in the router, as I have heard that this router is useless.  I guess it is time to look for a real one.  Any suggestions for a good router?

jim

NETGEAR...never any issue with anything on any of several that I have used over the years. Currently using WGT624 SuperG wireless router for the last 3 or 4 years. does 802.11b/g/SuperG (108Mbs), DHCP, NAT, WEP, WPA, Mac address filtering / reservation, etc. The MAC address reservation is really nice in that I can assign an IP for my laptop and effectively get static IP functionality (handy on my home network), while leaving the laptop itself set to DHCP for use in other places. Additionally, I am still using the WG511T pcmia card I bought with the router in my old laptop and, it too, has always (well except in the early stages of Edgy) "just worked" in Ubuntu.

---

### Post by seijuro on 2006-12-18
> **jpoRS said:**
> I followed the instructions I found in the Westell manual, Firfox and Internet Explorer both told me that the addresses I was requesting didn't exist.  Am I safe assuming that the problem lies in the router, as I have heard that this router is useless.  I guess it is time to look for a real one.  Any suggestions for a good router?

jim

If you're getting the same problem in windows then its definitely the router. As I mentioned earlier I have a netgear and I absolutely LOVE it. I even use it to back up my system when I play around with a dist-upgrade just zip all my files into one giant .tar and throw it across the lan onto the tower only takes a couple minutes for several gigs. I had a linksys prior to the netgear and it was terrible the firewall was a pita to configure and never worked the way I wanted not to mention it only allowed DMZ to be set to one of the 4 ports and not just any port it had to be the same physical port.

> The MAC address reservation is really nice in that I can assign an IP for my laptop and effectively get static IP functionality (handy on my home network), while leaving the laptop itself set to DHCP for use in other places.

I use this feature too. Indeed its very handy especially in conjuntion with dyndns so I can share stuff from my computer with friends and run any game servers I want.

---

