---
title: "apache configuration in ubuntu"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by gavakie on 2008-03-07
So I am brand new to Ubuntu and Linux I have had it on my machine for about 2 days.  I am trying to figure out how to confugre my machine so I can link the two domains I own to my computer and start writing some pages.  I have LAMP installed on 7.10 desktop edition.  Could someone point me to a page or give a newb some needed help.

---

### Post by Cypher on 2008-03-07
First and foremost ensure that Apache and all other components (PHP, MySQL, etc) are working perfectly fine locally. You can fire up Firefox and just use "http://localhost" for all of your testing. 

Once you're certain that everything is working, you'll have to do the following
[LIST=1]
[*]Registry with [DynDNS]("http://www.dyndns.com/services/dns/custom/") or [NoIp]("http://www.no-ip.com/services/managed_dns/plus_dynamic_dns.html")
[*]Configure your desktop with a static IP address
[*]Configure your router to forward all port 80 requests to your desktop
[*]Grab your DHCP (ISP given) address from your router and put that into your DynDNS or NoIP account
[*]Optionally use a software provided by the above 2 guys to keep your DHCP address updated with them, so that your domain will always work
[/LIST]

The only issue here is that these 2 guys offer free services as long as you use their domain name, if you want to use your own domain name, then you'll have to go for the paid services..

---

### Post by drubin on 2008-03-07
Just to add to the point 5)

Most new routers come with DHCP and you can set up the account on the router and when it's IP address changes it updates the  NOIP/Dyndns.

Good luck can be fun

---

