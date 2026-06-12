---
title: "Getting Linux Lamp Server To Allow Request From Internet"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by clee on 2006-08-31
anyone know how to get the ubuntu linux lamp server to prosess request from the internet becasue my server wont :( is it the built in firewall stopping it? please help me!

Thanks very much,
Chris

---

### Post by Bachstelze on 2006-08-31
Nope, it's just Apache config. IIRC, you need to comment out the * listen 127.0.0.1* line in Apache' config file.

---

### Post by Klaidas on 2006-08-31
The firewall might be blocking port 80, which you should open.
I don't know how to do that with iptables from terminal, but in Firestarter (GUI) it's very simple

---

### Post by clee on 2006-08-31
sorry i fergot what file the ip address is in please can you tell me it?

---

### Post by Bachstelze on 2006-08-31
I'm not on my comp right now but it must be something like /etc/apache2/apache2.conf

---

### Post by Sam Fisher on 2006-08-31
Sort of related to what I need to know. I have apache etc serving through the internet and all required ports forwarded on my router. However SQL will not allow external connections to my databases. How can I fix this?

---

### Post by clee on 2006-08-31
how do i allow connections from the internet to linux then ? what command do i need?

---

### Post by Jerome36 on 2006-08-31
Do you have a static IP address, and have you registered it with a DNS?

---

### Post by clee on 2006-08-31
I have run a webserver off of my internet connection befor and it worked fine, im trying out linux as the os, my ip is not static its dynamic, using no-ip.com to link to the ip but i asked my friends to see if they can access it but they say no they carnt see it:confused:

---

### Post by az on 2006-08-31
> **clee said:**
> anyone know how to get the ubuntu linux lamp server to prosess request from the internet 

It does that by deafult, out-of-the-box.  Apache starts serving the minute it is installed and it listens to the network - you do not have to config anything.

If you are running a desktop on that box, can you see apache by browsing localhost?

Does your ISP block port 80?  Usually, unless you pay for a business-type connection, they don't want you to run a webserver from your house.

Do you have a router?  Are you forwarding requests from the internet on port 80 to your apache server box?


> **clee said:**
> 
is it the built in firewall stopping it? please help me!


Chris

The built-in firewall does nothing by default.  Ubuntu deosn't install anything that listens to the network by default.  That has nothing to do with any firewall.

---

