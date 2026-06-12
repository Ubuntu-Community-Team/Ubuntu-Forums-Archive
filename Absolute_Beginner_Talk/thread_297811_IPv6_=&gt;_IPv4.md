---
title: "IPv6 =&gt; IPv4"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Nameless One on 2006-11-11
Everything is running fine in Xubuntu except for the Internet.
I have a 'D-Link DSL-502T' ADSL Router connected via Ethernet to my nForce something network card. I found after some searching on the internet that D-Link routers don't support IPv6, so I followed the instructions at [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4").
I managed to get Firefox working by changing the 'network.dns.disableIPv6' value under 'about:config' from false to true and I assume I have managed to disable IPv6, as the output from 'ip a | grep inet6' is blank.
Yet programs such as Gaim, Synaptic or the Update Manager still cannot connect to the internet unlike Firefox.
In Windows, everything connects perfectly to the internet, and I can access through an old Mandrake LiveCD.
How can I get my other programs to connect?

---

### Post by xpod on 2006-11-11
Wow,i thought i was the only sorry git on here who had a working copy of M.e in the house.....well,the only one who would admit it anyway.;)  

Dont really know how to help you but have you tried just leaving it as it was?
When i changed that to "true" on this machine it just made FF slower im sure.
It was supposed to do the opposite.Alledgedly.

Good luck regardless.Hope you suss it out.

---

### Post by Nameless One on 2006-11-11
I've simplified my question down to "How do I get programs to use IPv4 and not IPv6?".

---

### Post by Nameless One on 2006-11-12
After following the instructions at [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") and my programs still didn't work I was stumped. So I searched around the forums till I found a trick to temporarily fix the problem.
I went (in Xubuntu 6.10) Applications->System->Networking, clicked on the DNS tab, removed all the current entries and added these two addresses: '202.27.158.90' and '202.27.156.72'.
These addresses are the Primary and Secondary DNS server addressess, respectively, for my ISP, Xtra, in New Zealand. After changing this, things started to work for that session but soon returned to their prior state.

---

