---
title: "Apache Works.. Other PCs on Internal Network Dont See Apache Web Page"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by DaveLG on 2006-11-21
I have set up apache2 and php using Ubuntu 6.10.

From the apache server PC I can get to the standard apache default page and other pages via [http://localhost](http://localhost) etc. I can even get to my router set up [http://192.168.1.1](http://192.168.1.1) and then the internet

I cannot get to the apache server default page by typing [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1) from any other PC on my network connected through the router (192.168.1.1).

All the PCs on the network, including the server PC,  can reach the outside internet via the router. 

I think there is something simple that I have overlooked or done  incorrectly.

Any ideas...Thanks... Dave

---

### Post by Bachstelze on 2006-11-21
If you use 127.0.0.1, the machine will try to connect to itself, so obviously it will work only on the machine the server runs on. To connect to it with another one, type the IP address of the one the server runs on.

---

### Post by DaveLG on 2006-11-21
> **HymnToLife said:**
> If you use 127.0.0.1, the machine will try to connect to itself, so obviously it will work only on the machine the server runs on. To connect to it with another one, type the IP address of the one the server runs on.
Ok. I understand. Thanks.

---

### Post by DaveLG on 2006-11-21
I changed to a static IP address 192.168.1.144 but that didn't work. I rebooted the server too.

Now I use DHCP and I know the IP address of the Ubuntu server PC is 192.168.1.104

I can ping the server OK from Windows PC.

---

### Post by DaveLG on 2006-11-21
Wel I solved it. I needed to edit the ports.conf file. I addded:
Listen 192.168.1.104:80 

Now I can get to the server from other PCs on my internal network.

I have a dynamic IP ADDRESS from my DSL provider. I willnext try those dynamic IP services that will allow me to reach my server from the outside world.

Dave

---

### Post by Guiness on 2007-12-29
I'm having the same problem, Dansguardian blocks any incoming access to the webserver.

Is this the one you mentioned that fixed it?  /etc/apache2/ports.conf
If I add my ip as Listen internalIP:80 I can't even access the internet. I tried sticking the external port forwarded IP of the router and still no luck.

If I disable dansguardian then the web server works, but this is not a good idea.

---

