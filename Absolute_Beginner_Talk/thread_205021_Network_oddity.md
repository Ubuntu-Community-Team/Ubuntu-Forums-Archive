---
title: "Network oddity"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by wych77 on 2006-06-27
When I'm in XP my net connection works fine, however, when I boot into linux the only page I can get to come up on firefox are these forums and it takes a bit for them to load.  I have disabled/enabled my network connection twice now and it says it's active, however, I can't go to any other webpages.  Any help?

---

### Post by wych77 on 2006-06-27
I can download updates with no problem, however, I am unable to surf the net.  Anyone?

---

### Post by coffeecat on 2006-06-28
This might be the IPv6 issue. Here's a quick way to check: type 'about:config' in the firefox address bar (without the quotes). Now 'ipv6' in the filter - again without the quotes. You should be seeing 'network.dns.disableIPv6'. Change the 'false' value to 'true'. I guess you need to close down firefox and restart it.

If that fixes it, I suggest you read [this thread](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6+firefox). It starts as an excellent howto for disabling IPv6, but turns into a very interesting and useful debate.

Some routers are confused by IPv6 addressing, and I solved this issue by updating the firmware in my router but, of course, you can only do that if the manufacturer has actually bothered to develop decent firmware.

---

### Post by HereInOz on 2006-06-28
It is also possible that your modem/router is not assigning the computer's IP address via DHCP, or not relaying the DNS server addresses.  I have a Netcomm modem which is quite happy with assigning an IP address and DNS relay to a Windows box, but will not assign one if the same box is booted to Ubuntu.

The only way around this that I have found is to set the IP address static and set your DNS servers static in System > Administration > Networking.

It does sound a little like a DNS problem.  Hope this helps.

Cheers,
Alan.

---

### Post by wych77 on 2006-06-28
Thanks alot all.  I will try this out when I get home later.  The odd thing is, it worked fine until I tried to update the firmware for the modem, which Qwest has not made, lol.

---

### Post by wych77 on 2006-06-28
[QUOTE=coffeecat]This might be the IPv6 issue. Here's a quick way to check: type 'about:config' in the firefox address bar (without the quotes). Now 'ipv6' in the filter - again without the quotes. You should be seeing 'network.dns.disableIPv6'. Change the 'false' value to 'true'. I guess you need to close down firefox and restart it.

If that fixes it, I suggest you read [this thread](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6+firefox). It starts as an excellent howto for disabling IPv6, but turns into a very interesting and useful debate.

Some routers are confused by IPv6 addressing, and I solved this issue by updating the firmware in my router but, of course, you can only do that if the manufacturer has actually bothered to develop decent firmware.[/QUOTE]

Disabling solved it!  Thanks a ton *hugs*

---

