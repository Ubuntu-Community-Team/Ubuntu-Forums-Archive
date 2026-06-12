---
title: "network setup 2"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by tbrooke on 2008-01-28
I am trying to setup my network and I am confused about a few things:

I setup  a static address 192.165.1.109
subnet mask 255.25.255.0
gateway 192.168.1.1   <- my router

host name Ubuntu   I left domain blank

I have a couple of DNS addresses under DNS 

Do I need a local DNS server? I tried loading bind9 and since I couldn't get to the internet it failed

I have previously setup nfs and it works, I can connect via vnc to 192.168.1.109 but I can not use any names and my server cannot connect to the internet -
 I also added 192.168.1.109 and ubuntu to host  I also have samba running and host shows both Ubuntu and Ubuntu.workgroup since workgroup is my domain for samba

I feel like I missing something basic -- Any ideas?

---

### Post by mikeyphi on 2008-01-29
Is this a local network or to the Internet?

subnet mask 255.255.255.0? (typo?)

Routers often use DHCP - but I see you want a static.
Are you sure gateway is 192.168.1.1 and not 192.168.0.1 ??

If it's a local network - a Domain name is needed

Try using 194.119.131.65 as the local DNS server

---

