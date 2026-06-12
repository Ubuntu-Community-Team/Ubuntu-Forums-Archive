---
title: "networking"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by alexroot on 2006-12-16
hello.

i installed ubuntu server and it has a fixed ip in my LAN. The thing is i want to connect to it from home through the internet. what do i need to do in order to be able to use putty and connect to it?

thanks in advace.



edit: i forgot to mention that i can already connect to it through ssh but from within the network only.

---

### Post by Scorpuk on 2006-12-16
If you can connect to it through your local network then everything is go.

All you need to do is:

1. Know the IP address or DNS name of your internet connection. 

2. Forward the port SSH is on to your linux box, if you are behind a router / firewall. I think this is usually 22.

---

