---
title: "cannot access webserver through domain but can through IP"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by mnewbegin on 2007-06-04
I have had this problem on the webservers I have had before, but I need to fix this for work..

We have a ubuntu 7.04 server running apache2

when i type in

thedomain.com -> i get like dns resolution problems.

When i do a traceroute it shows the right ip address so the 2 are attached.

And from the outside world the domain is accessible.

inhouse is the only place not accessible.

for the mean time I have edited my 

windows xp hosts file 

to point


127.0.0.1       localhost
192.168.0.129	thedomain.com
192.168.0.129	[www.thedomain.com](www.thedomain.com)


i have gotten around this problem using another router with different ip addressing schemes also.

BUT WHAT IS THE FIX FOR THIS.

do I need a different subnet? or do i need to configure something differently?

---

### Post by lazyart on 2007-06-04
As far as I know that is quite normal.

---

### Post by phr0ze on 2007-06-04
Does your router have a loop-back setting? I know linksys usually do when you are dealing with internal services.

---

### Post by mnewbegin on 2007-06-05
im using a cisco 1720 so i will have to look in the readme on there page for configuration. im unlocking it tomorrow i have no clue what the password is on it. resetting it tomorrow.

---

