---
title: "Info on how servers work"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by appleimac on 2008-03-02
Hey guys I have setup a LAMP server Apache 2 php5 and mysql 

I have everything up correctly a when I go to 192.168.0.5/webstudiofx I can see what I have made so far for my new website.

I need to point my domain [www.webstudiofx.net](www.webstudiofx.net) to my new server and once I have done that what files do I have to edit to get the domain to point to the directory with my new website in webstudiofx



Many Thanks

---

### Post by rapiscan on 2008-03-02
First, you need to determine if apache is running correctly.  Go directly to the IP (192.168.0.5) and see if you get a basic webpage being served from apache.  If that's working fine, you know that apache is serving files fine.  You can then set up a virtual host for your domain   A Virtual Host simply allows you to direct incoming traffic for a certain domain to a place on your file system (so that the specified files are served when someone types in the domain).

Here is the documentation for a VirtualHost:
[http://httpd.apache.org/docs/1.3/vhosts/](http://httpd.apache.org/docs/1.3/vhosts/)

This section of the Ubuntu LAMP documentation goes over virtual hosts.  I recomend reading everything about apache though.
[https://help.ubuntu.com/community/ApacheMySQLPHP#head-8c16bcd2517fa5b9fa35d616f00d3bb59e981373](https://help.ubuntu.com/community/ApacheMySQLPHP#head-8c16bcd2517fa5b9fa35d616f00d3bb59e981373)

Regarding your domain, I recently gave a brief explanation of DNS in this thread:
[http://ubuntuforums.org/showthread.php?t=710237&highlight=rapiscan](http://ubuntuforums.org/showthread.php?t=710237&highlight=rapiscan)

I think reading through that post will give you a better idea of what you need to do in order to get your domain pointing to your server.

---

### Post by appleimac on 2008-03-02
Thanks you very much I will read all the links after work tomorrow :-)

---

