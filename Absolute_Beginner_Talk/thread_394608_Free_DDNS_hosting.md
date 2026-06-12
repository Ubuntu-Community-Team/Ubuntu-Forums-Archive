---
title: "Free DDNS hosting?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-03-27
We have surveillance cameras and we want to upload the camera outputs to the internet. I do not know more details, but according to the one who is setting this whole thing up, we need to change our internet service provider. 

I have a very efficient internet service provider but we have to change it because in order to upload the camera outputs, we need a static IP adress which my present ISP doesn't provide. 

I heard that all we need is a ddns host. Is that true? 

I found this ddns hosting site [http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/) but I am not sure if it is reliable and if it is actually free with no strings attached. Would you reccomend that ddns host? If you would not, can you point me to a reliable free ddns host?

---

### Post by lamalex on 2007-03-27
i use dyndyns.com with no problem at all.

---

### Post by hyper_ch on 2007-03-27
I use no-ip.com... same service as dyndns :) works great

---

### Post by wersdaluv on 2007-03-27
Are those absolutely free with no strings attached?

---

### Post by lamalex on 2007-03-27
depends what you want to do, they have more advanced pay-for services, but dynamic dns is totally free.

---

### Post by wersdaluv on 2007-03-27
Ohh. What I am going to do is not that advanced. Actually, it's not even for office. It's just for a residence. 

Do you think the free ddns hosting will do the job of uploading videos from surveillance cams to the internet?

---

### Post by halitech on 2007-03-27
ddns servers won't do anything as far as uploading images to the net, it will just simply give you a static hostname for a dynamic IP address. I've used no-ip and dynu.com and both are free and work well but you would still need to have a webserver of some sort running on your computer for it to be of any use.

---

### Post by medley on 2007-03-27
> **wersdaluv said:**
> Ohh. What I am going to do is not that advanced. Actually, it's not even for office. It's just for a residence. 

Do you think the free ddns hosting will do the job of uploading videos from surveillance cams to the internet?

DynDns is excellent....I've been using them for about 4 years now, and this is the free service. You normally have to run a client on one workstation on your network to update dyndns servers as to any changes in your IP address. I don't know if they have a Linux client or not. That being said, my Linksys router actually supports dynamic IP changes via dyndns, which would preclude your having to run a client application on a system on your network.

Bottom line: it works extremely reliably. I've never had a single problem in 3 or 4 years.

---

### Post by wersdaluv on 2007-03-27
Thank you for that. I will tell my electrician who is working with the camera project that we don't have to switch to another isp anymore if static IP is the only issue.

---

### Post by medley on 2007-03-28
> **wersdaluv said:**
> Thank you for that. I will tell my electrician who is working with the camera project that we don't have to switch to another isp anymore if static IP is the only issue.

One more thing you can do so that you don't have to use DynDns' domain name; buy a domain name with a registrar like EasyDNS that offers you the ability to route any requests for access to your domain to you dyndns account. You can cloak the re-route, so when your customer type in, say, [www.yourdomain.com](www.yourdomain.com), the request is rerouted to yourdomain.dyndns.org:portwhateveryouwant. The end user never sees the reroute, and you can specify a nonstandard port.

Good luck.

---

