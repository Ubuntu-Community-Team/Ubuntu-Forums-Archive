---
title: "Strange problem with internet connection"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by luisrobles on 2006-08-25
The problem is: when y get a ppp connection (username and password connection) after a little while, the browser (opera, Firefox) don't show any webpage, but MSN (amsn, gaim) and IRC work great. The installation was clean and after that i use automatix for some software.

Any idea for this problem?


Thanks!!

---

### Post by benfindlay on 2006-08-25
If messenger is working ok, it sounds like it's your DNS server thats the problem.

Sorry if this seems really patronising, but in case you don't know, DNS is responsible for converting ip addresses into the website address you type.

For example: www.yahoo.com's ip address is 209.73.186.238

Your DNS server performs the relevant look-up when you type the web address in, and allows the data to be fetched from the ip address.

I would check that the DNS listed is the i.p address assigned to the router/modem (most likely 192.168.1.1). If this is already the case, then it is worth logging into your router and retreiving the actual DNS address the router/modem uses externally.

Of course, if this has just come on suddenly, it may simply be that your ISP is currently performing maintenance, adn teh DNS servers are simply down temporarily (happens to me all th time, so I use an alternate DNS.

Hope this helps

---

### Post by luisrobles on 2006-08-25
> **benfindlay said:**
> If messenger is working ok, it sounds like it's your DNS server thats the problem.

Sorry if this seems really patronising, but in case you don't know, DNS is responsible for converting ip addresses into the website address you type.

For example: www.yahoo.com's ip address is 209.73.186.238

Your DNS server performs the relevant look-up when you type the web address in, and allows the data to be fetched from the ip address.

I would check that the DNS listed is the i.p address assigned to the router/modem (most likely 192.168.1.1). If this is already the case, then it is worth logging into your router and retreiving the actual DNS address the router/modem uses externally.

Of course, if this has just come on suddenly, it may simply be that your ISP is currently performing maintenance, adn teh DNS servers are simply down temporarily (happens to me all th time, so I use an alternate DNS.

Hope this helps

Thanks pal, but...how can do that? (im so noob) ](*,) i use pppoeconf to bringing my connection up

---

### Post by Iowan on 2006-08-25
As if you needed another possibility... **ipv6** has been known to cause problems with DNS.  I don't know how/if MSN and IRC use DNS. I'll leave you to search for info on disabling **ipv6**.

---

