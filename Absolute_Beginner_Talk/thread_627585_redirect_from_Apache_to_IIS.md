---
title: "redirect from Apache to IIS"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Sunbeam2007 on 2007-11-30
Hi everybody:

I don't know much about linux. I have some .net web applications runing on IIS (win 2003), what I want to do is to increase the security of my applications. I am planning to set up a linux web server that is going to be public, an redirect the requests to the IIS server (that is going to be private). The linux server will state public to internet (so people can visit my sites) and the IIS will state internal. My question is: what is the best way to implement that environment and where I can find some documentation to set it up, also which distro of linux would be the most appropiate.


Thanks in advance.

---

### Post by ukripper on 2007-11-30
Choosing distro is personal choice. I have ubuntu webserver running with LAMP setup.
This may help 
[http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-lamp-server-installation-with-screenshots.html)

Here is the server guide
[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

Security related thread [http://ubuntuforums.org/showthread.php?&t=510812#post3088372](http://ubuntuforums.org/showthread.php?&t=510812#post3088372)

---

### Post by plyrh8rofthyr on 2007-11-30
Apache module mod_proxy

This module provides for an HTTP 1.1 caching proxy server. so you would Put the ubuntu LAMP server on an outside facing place and leave the IIS server on your intranet, and configure mod_proxy on the apache system

---

### Post by KCPokes on 2007-11-30
> **plyrh8rofthyr said:**
> Apache module mod_proxy

This module provides for an HTTP 1.1 caching proxy server. so you would Put the ubuntu LAMP server on an outside facing place and leave the IIS server on your intranet, and configure mod_proxy on the apache system

Just to add to this.  Do a search for Proxypass (and Proxypassreverse) and you'll find some examples on how to set up your rules to forward traffic back to your IIS server.  It is a pretty simple process, made easier with some examples.

---

### Post by Sunbeam2007 on 2007-11-30
Thanks guys for you help. 

But I forgot another thing, my web sites uses FTP and Mail that are also configured  in the same server, and they consume some thrid-party web services, If I keep the IIS server on the intranet, what is gonna hapend with that services?

---

### Post by ukripper on 2007-11-30
> **Sunbeam2007 said:**
> Thanks guys for you help. 

But I forgot another thing, my web sites uses FTP and Mail that are also configured  in the same server, and they consume some thrid-party web services, If I keep the IIS server on the intranet, what is gonna hapend with that services?

If you wish to create standalone FTP services, this may be helpful [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

---

### Post by KCPokes on 2007-11-30
> **Sunbeam2007 said:**
> Thanks guys for you help. 

But I forgot another thing, my web sites uses FTP and Mail that are also configured  in the same server, and they consume some thrid-party web services, If I keep the IIS server on the intranet, what is gonna hapend with that services?

Depends on how they are being used, really.  FTP out, or FTP in?  With mail, I assume you are just sending mail out, which will not change.  Your biggest hurdle is services that people have to interact with directly; sending mail out will still work and ftping to another site would still work.  Anything that needs to hit that box directly will need to be investigated for solutions.

---

