---
title: "firefox web browser not displaying web pages"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by vikraman on 2007-12-25
hi, greetings to all.
I am a newbie to ubuntu and I have installed ubuntu  7.10 as my second operating system. It detects my netcard, i am able to configure the ip address for my ADSL modem etc., but the firefox could not display web pages. It shows 'server not found ' error for all the web pages. But when I installed kubuntu on the same machine I am able to view the web pages over konqurer web browser. I want to use only ubuntu 7.10. But how to troubleshoot the firefox so that i can view web pages?

---

### Post by ubutufan on 2007-12-26
Give static address to your machine
Next use the correct subnetmask
Enter the gateway (ip of your router)
For DNS use the same ip of your router

Let us know

---

### Post by vikraman on 2007-12-26
Hi, I have done that. When I ping 192.168.1.1 it is succesful without any loss and firefox is able to open my smartAX MT882 ADSL modem web page by typing [http://192.168.1.1](http://192.168.1.1) where i configured my user name pass word etc., and dignostistic test also sucessful. everything ok except firefox does not display any web pages and returns server not found error

---

### Post by cub682 on 2007-12-26
Disabling IPv6 might help.

[http://rojs-techcorner.com/blog/2007/07/27/speed-up-firefox-on-linux-disable-ipv6-lookups/](http://rojs-techcorner.com/blog/2007/07/27/speed-up-firefox-on-linux-disable-ipv6-lookups/)

---

### Post by vikraman on 2007-12-27
hi, done that. still no use

---

### Post by vikraman on 2007-12-27
> **vikraman said:**
> hi, done that. still no use

if I put the ip address of a website it opens. for example i typed [http://10.240.43.216](http://10.240.43.216) it displays the web page. if I type [www.google.com](www.google.com) it does not open.

---

