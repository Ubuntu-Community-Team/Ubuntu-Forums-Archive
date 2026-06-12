---
title: "[SOLVED] Changing the IP address that Apache/PHP/IRCd uses."
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by `Jon on 2008-03-24
Hey.

I've installed PHP/MySQL/Apache/UnrealIRCd on my machine over the last two days, and everything works great. The only problem is, I can only connect to these things through localhost or the IP address 127.0.0.1, which is not accessible from other computers.

If I go to [http://showip.com](http://showip.com), it says that my IP address is 92.232.176.83.

Is there a specific reason why this is happening? Or have I managed to break something else? lol

Thanks for any help I receive. 

Jon.

---

### Post by penguinpi.com on 2008-03-24
Are you connected to the Internet through a router? Make sure you have port 80 forwarded. You're going to have to give some more details if thats not the case.

---

### Post by .nedberg on 2008-03-24
Both localhost and 127.0.0.1 point to the machine you are on at the moment.

try

```

ifconfig

```
in a terminal. It will give you your local IP (probably in the form 192.169.1.x), use that on a different computer on the same LAN.

---

### Post by leroyc on 2008-03-24
Now here are few ideas:

If you are behind a router, make sure you have enabled Port Forwarding.

The best idea is to enable all ports to be forwarded to your IP.

If you type in console:

```
ifconfig
```

You will see something like:

```
eth0      Link encap:Ethernet  HWaddr 00:1B:24:2A:8C:CD
            inet addr:192.168.4.123  Bcast:192.168.4.255  Mask:255.255.255.0
            inet6 addr: fe80::21b:77ff:fe28:f2bd/64 Scope:Link
```

The inet addr: is the local IP you have. Make sure you set in your Router to port forward the following ports to your internal IP:

Apache: 80
MySQL: 3306
IRCD: 6667 and 6668

I believe afterwards you will be able to connect from outside.

Note: make sure you dont have the ports blocked:

iptables -L | grep 80 
iptables -L | grep 3306

---

### Post by .nedberg on 2008-03-24
If you need help portforwarding try [this page]("http://portforward.com/")

---

### Post by `Jon on 2008-03-24
I am connecting to the internet through a router, and I -thought- I had Port 80 forwarded. This is the settings page of my router:

[img]http://img143.imageshack.us/my.php?image=screenshot1nb3.png[/img]

.nedberg: I get an inet address of 192.168.123.100

---

### Post by .nedberg on 2008-03-24
> **`Jon said:**
> 
.nedberg: I get an inet address of 192.168.123.100

That is normal! If you have another computer on the same LAN you could try to connect to that IP to see if everything works as it should.

---

### Post by `Jon on 2008-03-24
Hey.

I found the problem; I was forwarding ports to my router page, and not my actual computer. When I changed the last 3 digits to those of my computer, it all works. 

Thanks for the help! :D

Jon

---

