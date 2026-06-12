---
title: "ssh only accessible from internal IP"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by ejbrever on 2006-11-03
Hi,

I have a server that is used for VPN, so it is attached to an external IP and an internal IP. I would like to make it so that I can only ssh into it using the internal IP (for security purposes). Is there a way to prevent ssh from allowing connections on one of its IP's?

Thanks for the help,
Eric

---

### Post by IYY on 2006-11-03
It's called port forwarding, and is done in the router, not the OS. The router's IP is often 192.168.0.1 or 192.168.1.1

You need to forward port 22 to the local IP of your machine.

---

