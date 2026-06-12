---
title: "can't surf"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by gravediggers on 2005-10-31
Hi,
Just new to Ubuntu. Have broadband connection with DSL via NB5 modem with primary PC on Windows XP able to work OK.
Second PC with Ubuntu on a second port on the router and can ping various IP addresses, but times out when http to same sites. Am I missing something?

---

### Post by rmjokers on 2005-10-31
Are you using the IP address or the hostname to get to the http servers?  It sounds like the Ubuntu box may not be getting the DNS information it needs to resolve the IP addresses.  The current DNS server information should be in 

/etc/resolv.conf

If this file is empty or contains the wrong entries, you will have problems.

---

### Post by kagashe on 2005-10-31
[QUOTE=rmjokers]Are you using the IP address or the hostname to get to the http servers?  It sounds like the Ubuntu box may not be getting the DNS information it needs to resolve the IP addresses.  The current DNS server information should be in 

/etc/resolv.conf

If this file is empty or contains the wrong entries, you will have problems.[/QUOTE]Also check the permission of this file.

kagashe

---

### Post by gravediggers on 2005-10-31
Thanks guys. Not as sinister as it seems. I don't know how many times I looked at my network settings and didn't notice it, but when I looked at the DNS address as you suggested, it was obvous. The automatic setup had put the address of my router as the primary DNS. Substituted  the real ones and is cool!:D

---

### Post by gravediggers on 2005-11-04
:mad:  wtf!..just went to come to this forum and same problem again. I have just put the correct DNS setting in again, but why would they have changed?! Is there something else happens (maybe on reboot??) that causes the setting to be updated? The DNS address was my router address!:confused:

---

### Post by rmjokers on 2005-11-04
If you go to System->Administration->Networking and look at Ethernet connection properties, what do you see?

For connection settings, you should have Configuration: DHCP and no other options set (unless you use manual addressing)

---

### Post by gravediggers on 2005-11-05
Correct, that is what i see, but it is not the DHCP that is the problem, it is the DNS. Once again it has reverted to dragging in my router address, instead of my ISP's DNS server address that I set it to.

---

### Post by spizkapa on 2005-11-05
[QUOTE=gravediggers]Correct, that is what i see, but it is not the DHCP that is the problem, it is the DNS. Once again it has reverted to dragging in my router address, instead of my ISP's DNS server address that I set it to.[/QUOTE]

If you're using dhcp, then you get the settings for DNS when you boot up (or restart the networking) so that's why your settings are removed each time. It's your router that needs to know the dns servers of your ISP and you will then get them as normal when you dhcp. Check your router's settings.

HTH.

---

### Post by gravediggers on 2005-11-05
OK....can't seem to find somewhere in my router settings for the DNS addresses. I assume that my router would normally forward outgoing traffic to my ISP and they would do the DNS lookup. The other machine (Windows XP) specifies both obtain IP address automatically (DHCP) and obtain DNS address automatically. My linux box is set for DHCP, and I follow your argument, so why wouldn't it obtain the DNS in the same manner. By the way, my router is a Netcomm NB5.

---

### Post by gravediggers on 2005-11-09
Well, I finally figured it out. I knew it should work with nameserver=myrouterIP and so tried pinging a few sites using their domain names and got replies. OK, so the problem is firefox.tried looking for connection and other setting that might help, tried a few things, but no joy. Read a post on mozillazine that suggested typing about:config in the location bar, finding the entry for network.dns.disableIPv6 and toggling that to true. :) Great - it works! BTW, any one know why?

---

