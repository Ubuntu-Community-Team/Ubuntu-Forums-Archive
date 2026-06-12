---
title: "Host and Domains!!!"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2006-10-05
A question!

When I used to have a windows networking i used to be able to find the computers my there host names insted of there ip.

But now it dose not.

I have a ubuntu server acting as a router

My servers name is apollo and one of the others is mars and another on is columbus.

There other machines get there IP's by dhcp, this makes it annoying when I want to do things, ssh etc.

Can anyone help me out???

---

### Post by llamakc on 2006-10-05
Edit the file /etc/hosts and add your machine names to it.

IP.OF.A.PC   pcname

---

### Post by guysmiley25 on 2006-10-05
Cool chears for that it help with the server, but what about the client machines cause there IP changes.

---

### Post by llamakc on 2006-10-05
Don't use dhcp and assign static IP's.

---

### Post by guysmiley25 on 2006-10-05
That might be the way I have to go in the end, but it is just much easier to manage the computers by name rather than IP.

It used be all good when we were using clarkconnect as a router and dhcp server. when a machine got its IP the clarkconnnet box got the host name and then added it to its DNS thing. however it wasnt a DNS server. it jsut passed the host names and then forward the rest to the ISP DNS server.

We decided to use the ubuntu server insted of clarkconnect cause we wanted more than just a router out of that one machine.

So I have reason to think that it can be done. maybe I need to have a DNS server as well and some how link it with the DHCP but i'm not sure.

any thoughts?

---

### Post by guysmiley25 on 2007-05-09
bump!

I thought about installing an DNS server, but I'm not too sure what I doing with it. Also I can not see how the get the host names from the host machines!

Any Ideas?

---

