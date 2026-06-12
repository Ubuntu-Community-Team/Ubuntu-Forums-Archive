---
title: "server to public"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by zombietls on 2006-08-25
how would i get my webserver to be able to be viewed by pulic with the domain name that i have bought.

---

### Post by echo $USER on 2006-08-25
You need to get it registered with DNS servers.

---

### Post by zombietls on 2006-08-25
if i bought a registered domain name doesnt that count ??

---

### Post by Jerome36 on 2006-08-25
Did you get a static IP from your ISP?

---

### Post by zombietls on 2006-08-25
would i be able to find it in the router and if so what do i do with it, but i do believe i have one

---

### Post by Jerome36 on 2006-08-25
Well first off you'll need a static IP address, so you'll have to make sure you have one.  Odds are if you're not sure you probably don't have one.  That's something you'd KNOW you're getting, when you setup an account with an ISP, and you pay for it.

You need your IP address registered with a DNS, so computers will know that [www.yourdomainnamehere.com](www.yourdomainnamehere.com) points to whatever your Static IP is, that your ISP reserved for your machine.

Also, if you have a router you'll have to set up the router to send port 80 traffic to your new server.

---

### Post by zombietls on 2006-08-25
so in order to send traffic through port 80 how would i go about port forwarding it, would i just send it to my static ip ??

---

