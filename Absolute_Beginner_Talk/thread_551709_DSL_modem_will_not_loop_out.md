---
title: "DSL modem will not loop out"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by siege911 on 2007-09-15
So I set up a webserver with Ubuntu and ISPConfig at my house and it's working properly... however:

My DSL modem (Actiontec) does not loop out so whenever I try to visit my website from my home office, it brings me to the DSL Modem settings menu. When I access it from my work, I can get the website just fine. I was told that this is a problem with my particular DSL Modem and there's no way around it (aside from purchasing a new modem.

Also, I have multiple sites setup so I can't just simply type the local IP address as it pulls up the Shared page.

Is there any tricks or things I can do to pull up my website from my local network? Anything like 192.169.0.1:mydomain.com or something like that? Or do I just have to go buy a new modem? I'm not sure if setting it up as a DNS server will fix it (my DNS is setup through a 3rd party) but at the moment, the DNS stuff is way over my head (this is my first webserver).

What can I do?

Thanks

---

### Post by 22bsti on 2007-09-22
what is the exact model of actiontec modem that you have, you should be able to set it to bridged mode and get a cheap router that does port forwarding and forward port 80 to your webserver, just make sure that if you do forward the port to your webserver that you statically assign the ip on your webserver or somehow make sure that your webserver always gets the same ip

---

