---
title: "Internet not working"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by halohunter on 2007-03-23
Hello,

Im a new user to ubuntu. I cant access the internet on ubuntu via my ethernet connection. The networking options panel states that I am connected to my network and I can successfuly ping my router and various websites such as google.com. However, if I try to access the internet via firefox or evolution, the connection times out.

I switch to XP and the internet works straight off.

Whats up?

---

### Post by Paul41 on 2007-03-23
I have seen other people with problems similar to this and it was a DNS problem. I can't remember what they did to fix it, but if you search the forums you might find something. If I can find where I have seen this before I will post it later.

---

### Post by afljafa on 2007-03-23
Type about:config in the address bar

Type ipv6 in the filter

Double click the line to change true to false.

Browse

---

### Post by HereInOz on 2007-03-23
Probably DNS,

Go to System > Administration > Networking and set your IP address as a static IP in the same subnet as your gateway router, set the gateway as the internal IP address of your router, and then click on the DNS tabs, and set the DNS addresses to those supplied by your ISP.

If it is a DNS problem, that ought to fix it.

---

### Post by Paul41 on 2007-03-23
If afljafa's suggestion allows you to connect with Firefox, but you still have problems with other things, such as Synaptic, you could try blacklisting IPv6.

[http://doc.gwos.org/index.php/DisableIPV6](http://doc.gwos.org/index.php/DisableIPV6)

---

### Post by justleen on 2007-03-23
can you use
```
 sudo apt-get update 
``` ?

---

### Post by afljafa on 2007-03-23
Given the fact that he can ping google.com suggests that it`s not DNS.

Pretty sure it will be the IPV6 setting.

---

### Post by HereInOz on 2007-03-23
Having read your post again, if you can ping [www.google.com](www.google.com) using the domain name rather than the IP address, it won't be a DNS issue.  If it was DNS, then it would not resolve [www.google.com](www.google.com) and the ping would not work.  That's the theory anyway.

Sorry for misleading you.

---

### Post by HereInOz on 2007-03-23
Yes, should have read the post more thoroughly the first time :-)

---

### Post by Paul41 on 2007-03-23
Don't feel bad HereInOz, I didn't notice that it was able to resolve [www.google.com](www.google.com) either so I am guilty also :) .

---

### Post by afljafa on 2007-03-23
> **HereInOz said:**
> Yes, should have read the post more thoroughly the first time :-)

How`s the weather over in Adelaide? I`m in Kalgoorlie and today was one of those rare cool sunny season changing days - lovely.

---

### Post by halohunter on 2007-03-23
Hey guys thanks for the help.

Despite being able to ping google.com, it was a DNS error. For some reason, the DNS server was set to my router local ip. I changed it manually to a different automaticaly discovered DNS and viola. It works.

---

### Post by afljafa on 2007-03-23
> **halohunter said:**
> Hey guys thanks for the help.

Despite being able to ping google.com, it was a DNS error. For some reason, the DNS server was set to my router local ip. I changed it manually to a different automaticaly discovered DNS and viola. It works.

Well there you go - odd. If you find pages taking a while to resolve - try the about:config trick.

---

### Post by i_a_coops on 2007-03-23
i have a similar problem - i can ping google.co.uk, but when i say set it to 5 pings only 2 of them work. what does this mean? Firefox won't connnect to the internet, but gaim can.... i've blacklisted ipv6, disabled it in firefox, and i really don't know what else to try.... i've been through all the options i can find in firefox! the internet connection works fine in mac os x ...... thanks!

---

### Post by i_a_coops on 2007-04-29
Well ipv6 is off in Firefox and it's blacklisted! Eek. thanks anyway. I only get 2/5 successful pings on average, and Gaim works sporadically at best.... any ideas? i can't even update packages or download a different browser to see if that works better! Should I just update to Feisty and see if it's fixed? Thanks.:confused:

---

