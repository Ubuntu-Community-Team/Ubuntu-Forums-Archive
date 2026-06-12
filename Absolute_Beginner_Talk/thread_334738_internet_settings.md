---
title: "internet settings"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by helphope on 2007-01-09
Hi there.
I'm trying to understand how the connection to internet works. (A friend of mine installed everything time ago), so lately I've been reading many how-tos and tutorials that I'm dreaming of TDL, primary Dns,  ... ](*,) 
If someone can help me please, in this:
1) if I'm right in saying that nameserver IP are the same as DNS server's IP addresses that my ISP provided to me;
2) how I can know these IP/nameserver
3) how I know my IP watching inside my PC (I know I can go to [http://www.ip-adress.com/](http://www.ip-adress.com/))

thanks for any help

PS: If anyone of you know a real step by step tutorial/guide for these questions

---

### Post by Modernity on 2007-01-09
What are you planning to do, that you need to know or change any of the information? It might help us give you a better understanding on what you are planning to accomplish.

---

### Post by MrHorus on 2007-01-09
> **helphope said:**
> 1) if I'm right in saying that nameserver IP are the same as DNS server's IP addresses that my ISP provided to me;

Yes.

> 2) how I can know these IP/nameserver

```
less /etc/resolv.conf
``` will show them in linux, otherwise ipconfig /all in Windows will show them, assuming your ISP uses DHCP.

> 3) how I know my IP watching inside my PC (I know I can go to [http://www.ip-adress.com/](http://www.ip-adress.com/))

```
sudo ifconfig
``` Will show any IPs assigned to any interfaces on your machine.

---

### Post by helphope on 2007-01-09
Thanks a lot for replying

> What are you planning to do
I'm trying to understand how the connection to internet is built.

```
less /etc/resolv.confwill show them in linux, otherwise ipconfig /all in Windows will show them, assuming your ISP uses DHCP. 
``` 
In /etc/resolv.conf there is nothing apart from the name I gave to my localdomain, that is > search mydomain.org

> assuming your ISP uses DHCP.
How do I know it?


> sudo ifconfigWill show any IPs assigned to any interfaces on your machine.
It doesn't show the IP I can see on a site such as  [http://www.ip-adress.com/](http://www.ip-adress.com/)

---

