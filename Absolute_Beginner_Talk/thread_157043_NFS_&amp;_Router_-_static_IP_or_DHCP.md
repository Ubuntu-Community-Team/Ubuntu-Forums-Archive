---
title: "NFS &amp; Router - static IP or DHCP?"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by damianubuntu on 2006-04-08
Hi,
I've just changed my modem for a router, and I believe I have to use DHCP with thee router, but my NFS shares are configured with static IP addresses.  Does anyone know whether either I can use static IP addresses with a router, or (more likely) how I can use dynamic ip addresses with NFS shares?
Thanks

---

### Post by patrick295767 on 2006-04-08
I set up this for my linux server.
  
All linux boxes are in DHCP.
  
The router is configured so that he is looking/checking the MAC addresses and giving the IP static to the server. 
  
That's the "best" & easiest way man !
"best", depending on what you wanna do of course ...& can be discussed... 

 Greetz

---

### Post by damianubuntu on 2006-04-08
Thanks,
I'm just beginning to find my way around the router config.  I've found that I can turn of DHCP and give use static IP addressing.  What's strange to me is that the routers own address by default is 192.168.1.1 , if I change this to e.g. 192.168.0.100, and set the computer to e.g. 192.168.0.1 instead of e.g. 192.168.1.2, and change the gateway as well, then I can ping the router, but not anything on the internet.  Change back the addresses and all is well.  Do I have to set up static IP routing?  or am I missing soemthing else?

Cheers

---

