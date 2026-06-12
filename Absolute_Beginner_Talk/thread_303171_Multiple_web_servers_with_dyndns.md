---
title: "Multiple web servers with dyndns"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by BryanM67 on 2006-11-19
OK..I was wondering if its possible to do this.  I am considering creating a Web Server using Ubuntu Server and Apache.  Since I have a dynamic IP address assigned by my ISP I would use dyndns so that my dns entry gets automatically updated every time my IP address is changed.

Since I run a cable connection which is somewhat fast, there are limits especially on the upload speed.  That can affect my website performance if I have tons of pictures.  So what I was thinking about doing is having multiple servers - each one in a different household and using dyndns.  I would take the necessary steps to ensure the web content of each server is identical.

My server would be the primary one but if my bandwidth is maxed out, I would like any new web requests to be redirected to one of the other two servers.  Furthermore if my server or connection goes down, I would like for there to be a way that web requests to my domain be automatically redirected to one of the backup servers.

I don't know if this is possible considering that all servers would be in different locations and are not in the same network.

Any opinions or suggestions are greatly appreciated.

---

### Post by NetworkGuy on 2006-11-19
I don't think what you want can be done with dyndns.  You need something like a load balencer to send users to the correct server based on bandwidth.

I manage some of these where I work, but I doubt you can afford something like that for your needs :)  (27K for the base model)

---

