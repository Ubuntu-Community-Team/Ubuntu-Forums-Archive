---
title: "DHCP Problem"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by phyxsly on 2007-04-12
Hi.

I am having problems connecting to the Internet using DHCP. I already configured the interface to work with DHCP and the Network proxy to direct connection. But still, it doesn't connect. 

Can anyone help me out here?

FYI, DHCP works fine in win xp. I am using ubuntu 6.10

Thanks

---

### Post by dbbolton on 2007-04-12
go to System > Administration > Networking. then, click the DNS tab. make sure your DNS Server is correct. it's probably the IP Address of the router, like 192.168.1.1

if this is correct but you still can't connect, set your router to allow all traffic (temporarily).

---

### Post by tankerman on 2007-04-12
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				totally new to this, hope this may help
[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)
have a look here at the ivp6 part, worked for me.
running 6.10 live disc at moment

---

### Post by phyxsly on 2007-04-13
I have done this a while ago and still i can't connect. Is there any other way to remedy this?

---

### Post by phyxsly on 2007-04-13
> **dbbolton said:**
> go to System > Administration > Networking. then, click the DNS tab. make sure your DNS Server is correct. it's probably the IP Address of the router, like 192.168.1.1

if this is correct but you still can't connect, set your router to allow all traffic (temporarily).

How will I set the router to allow all traffic?

---

### Post by alex_anthony on 2007-04-13
you have to log into it
in your browser type in the ip of the router in the address bar. You will probably have to log in, the details should have been given to you with the router (may be on a sticker on the router) It offers you the option in there of changing security. The layout varies between manufacturers

---

