---
title: "website password"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by wsetchell on 2008-03-19
So I'm trying to get my 1st website/server up and running.  I tried entering in my 
http:\\(my IP address) from another computer and I get prompted for username and password.  I don't remember setting these up, how can I change the user names and password that are available.  I want to let anyone access these files.

Using Ubuntu 7.10 and apache2

What and where exactly do I change things so that instead of entering in my IP address, people can just type in [www.example.com?](www.example.com?)

Thanks a lot

---

### Post by PeterJS on 2008-03-19
> **wsetchell said:**
> 
What and where exactly do I change things so that instead of entering in my IP address, people can just type in [www.example.com?](www.example.com?)

Thanks a lot

You'll need to purchase a domain name from a registrar, and have them point that name at your machine.

[http://en.wikipedia.org/wiki/Domain_Name_System](http://en.wikipedia.org/wiki/Domain_Name_System)

---

### Post by wsetchell on 2008-03-20
Okay so here is the newest set of problems I'm having.  I got access to my router so I can edit things.  What exactly do I need to change to allow port forwarding?

---

### Post by Cypher on 2008-03-20
Find your router in [this list]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm") and then find the application (WWW, SSH, FTP, etc) that you want to forward and follow the instructions.

---

### Post by wsetchell on 2008-03-25
Alright so I followed those instructions, but still no working server.  The instructions say, ip 192.168.1.__
with only the __ being able to edit.  I have 192.168.0.____ is something wrong here?

The other problem I can think of is maybe I'm giving the computer the wrong ip address to forward the site to.  What is the best way to find the ip of the machine that's running the server?

---

