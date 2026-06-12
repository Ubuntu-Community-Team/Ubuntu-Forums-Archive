---
title: "Network problem with Linksys router"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by guumby on 2006-06-05
I'm a beginner with linux and am quite stuck ](*,) with trying to figure out a network problem I am having.

I have a clean Dapper install where everything seems to work except the network.  My computer is a duel boot XP / Linux, and I have multiple XP machines on my home network with a mixed wired/wireless Linksys WRT54G router.  The Dapper machine is wired with an nvidia Ethernet controller (Asus A8N-E motherboard).

I'm pretty sure the ethernet is working because in Linux I can see the other XP machines on my network, connect to a networked hard drive, and access the Linksys web interface.  What I cannot do I ping or connect to the outside on the machine (I can with the XP boot).  I have tried DHCP and assigning an IP address, as well as installing nForce4 linux specific drivers, to no avail.

I would appreciate any and all help to figure this out.  Thanks.

---

### Post by sorrow777 on 2006-06-05
Things to try:

Ping your gateway ip
ping your primary and or secondary dns

ensure that /etc/resolv.conf has the correct information in it

---

### Post by guumby on 2006-06-05
I tried the suggested.  I also disabled IPv6 (some other posts mentioned it may cause interference or latency problems).

I was able to succesfully ping my gateway ip.  I was also able to succesfully ping my primary and secondary dns, and /etc/resolv.conf has the correct info in it.

I am also able to succesfully ping any ip address (ie. 72.14.207.99 for google.com and 82.211.81.166 for ubuntu.com).  However I am unable to resolve hostnames either via firefox or the command line - really strange.  So still no web browsing or apt updates.

Thanks for the advise but I'm still stuck.

---

### Post by sorrow777 on 2006-06-06
hmm... have you tried using "ip" to flush the routing tables? It sounds like something is messed up there for sure.

---

### Post by ProjectGod on 2006-06-06
another dns issue. i had the [COLOR=red]EXACT[/COLOR] same problem and it definately points towards dns configuration or lack of.
 
i guess what you'll need to do is log into the router and check your isp's dns server ip address... 
 
on your ubuntu machine put the server's address into the dns configuration section for the network adapter... 
 
or relatively if you've configured a DHCP network... make sure your DHCP server is configured to give out the ISP's DNS server address as well as it's own DNS server address... (assuming its also acting as the mini internal dns server)
 
hope this works. :mrgreen:

---

