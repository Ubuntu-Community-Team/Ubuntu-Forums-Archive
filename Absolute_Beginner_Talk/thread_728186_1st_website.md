---
title: "1st website"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by wsetchell on 2008-03-18
So I'm making my own website and going to be using my home computer as a sever.  I'm running Ubuntu 7.10, and using Apache.  Right now I have my .html files written, and apache installed.  This is what I'm want to do next:

1. buy a domain name [www.somename.com](www.somename.com) any suggestions of good places to buy this name at?

2. Somehow use apache to have somename.com reference the files on my computer.  This is where I need some help with.  I don't really know where to start.

Thanks a lot
Will

---

### Post by zerhacke on 2008-03-18
If you're using any ISP I know of without a business account they're going to block HTTP servers on the customer side at their router.  You will not be allowed to run a server from your home.  It makes good business sense, because they'll force you to pay for the business account instead of the residential, or they'll force you to buy a hosting package from them.  Either way it's considerably more expensive on your end as compared to residential service.

If I were you, I'd look into cheap hosting from a good host.  I pay less than 9 dollars a month for my hosting at Dreamhost.

---

### Post by lespaul_rentals on 2008-03-18
> **wsetchell said:**
> 1. buy a domain name [www.somename.com](www.somename.com) any suggestions of good places to buy this name at?

godaddy.com will do the job nicely.  You can also get DNS names for free, but they have other stuff after them like "yourname.dyndns.com".

[QUOTE=wsetchell]2. Somehow use apache to have somename.com reference the files on my computer.  This is where I need some help with.  I don't really know where to start.[/QUOTE]

All you need is your WAN IP address (the one that the Internet associates with you) and a service running on the other end.  A user will type your IP address (or the domain name once you buy one) into their web browser, and the web browser requests a web page.  Your router then processes the request over port 80, and asks the web server (your computer) for *index.html*.  The webpage is sent to the computer that requested it.

All you need to do is forward port 80 from your router to your internal IP address.  Any requests for information over port 80 will contact your Apache daemon, which will then transmit the webpages contained in */var/www/*.  Then, you will need to find out your IP address ([http://www.whatismyip.com](http://www.whatismyip.com)) and that is how people can view your website.  If you want a free domain name, try [http://www.dyndns.com](http://www.dyndns.com) and this domain name will always point to your WAN IP address, even if it changes.

---

