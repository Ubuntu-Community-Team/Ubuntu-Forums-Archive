---
title: "A Couple of Problems, Help much appreciated"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2006-07-03
First of all,

My gaim does not connect although i can ping google... I am using ADSL, and my router is a netcomm NB5Plus4

Is there any idea why that cannot be so?

I am using 5.04 Ubuntu.

Also, i cannot find Glib 2.0 Anywhere... Any help guys?

Many thanks in advance,
Kris

---

### Post by HereInOz on 2006-07-03
Firstly I think it is libglib2 in ubuntu - it is in Dapper anyway - it should be in synaptic.

If you can ping google but not access the google site from a web browser, it may be a DNS problem.  I have noticed that some Netcomm modem/routers do not like ubuntu, and flatly refuse to assign an IP address or DNS addresses.  Often in this case you have to set your IP as a fixed IP with the DNS servers from your ISP.

If you can access google from a web browser using the URL, then disregard all the above, as it is clearly not a DNS or DHCP problem.

The other possibility is a firewall issue.  Try installing firestarter and then turning off the firewall for a short while and see what happens.

Other than that, I can't think of much else without a bit more information form you.

Cheers,

Alan

---

### Post by Fac51 on 2006-07-03
your gaim doesn't connect to what?

---

### Post by Jagot on 2006-07-03
If you're still using 5.04 then I'd suggest upgrading to Dapper because this may fix some of your issues.

---

### Post by KrisDwyer on 2006-07-03
Thanks,

Turned out to be the DNS... I was using my router when in  fact i shouldve been using my ISP"s  DNS.

---

### Post by HereInOz on 2006-07-03
Just love those Netcomm router/modems.  They do it all the time :-)

---

