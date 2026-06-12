---
title: "Just installed Ubuntu Server, now what?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by mork on 2007-10-01
Hello,

I just installed Ubuntu server with no problems.

Is there a good reference manual or book someone can recommend that walks me though setting up a Website, email, DNS, and all the other stuff *using* Ubuntu?

I have that "new user, feeling clueless" feeling!

I found a Website that was modifying scripts on the second page. I think I need a more gentle introduction than that (I'm a software developer who is trying to learn setting up a server.)

I'm hoping Ubuntu is a good choice to manage multiple Websites using LAMP (and Tomcat).

Any help or suggestions would be appreciated.

Thanks.

:)

-- M

---

### Post by sitedesign on 2007-10-01
You can start with installing webmin or if you want a guide then look at:
[https://help.ubuntu.com/community/Servers?action=show&redirect=Server](https://help.ubuntu.com/community/Servers?action=show&redirect=Server)

[http://www.webmin.com/](http://www.webmin.com/)
If you download webmin using wget then install it with apt-get -i {package name}
It will failt based on the dependencies, so then at the terminal type aptitude, which will run the aptitude package manager. Type B to look for the webmin broken package and use shift + to install it which will fix the dependecies and then g and another g to install the packages.
Webmin is a very good tool for managing servers. Without having to understand too much of the command line stuff.

There are plenty of ducouments in the community documentation for doing most of what you want to do.

---

### Post by justleen on 2007-10-01
why on erath people want to use LAMP baffles me to no end.. Your on linux! install the packages!
(if im not mistaken, httpd/apache comes default with the server..)

as far as guides are concerned for a server.. have a look at the package  specific documentation, ([www.mysql.org](www.mysql.org) for mysql for example)

another goud place is the [ubuntu wiki,]("http://en.wikipedia.org/wiki/Ubuntu_(Linux_distribution)") and [ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty").

If you need specific help with installing/confiruing packages, let me know

as fas as mail is concenred, i advise postfix, instead of sendmail. postfix is  a lot easier to configure IMHO..

---

### Post by mork on 2007-10-01
Wow, great quick replies, thanks.

I suppose what I was trying to say is that I want some kind of reference material so I actually know what to type to accomplish a real task, not to edit a configuration file. I'm not an network or Linux admin (to say the least <g>).

Most of the documentation says to type this or that, but it's atomic (focuses on a small task) and doesn't relate to some complete task like setting up a Website.

What I'm hoping to find is a reference that says: "To set up a Web Server, do this...". Then, I'd like to be able to verify it works.

"To setup email, do this...." 

I'm a computer professional with almost some command line linux experience. I understand redirection, piping, many linux commands and the like. Setting up a server, uhhh,....

Most of the books I've seen focus on the desktop version, not the server version.

----

I also don't know basic things like...

1. Should I get an ISP account before configuring the server (that is, eeeek, connect the server to the Internet)?

2. Do I need to use a router? (The docs say that no ports are enabled by default, so why use a router?)

3. Other questions I haven't even thought of yet... <s>

-----

Look forward to replies.

Thanks again.

- M

---

### Post by hyper_ch on 2007-10-01
For a complete hosting solution have a look here:

[http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704)

Detailed step by step description.

---

### Post by mork on 2007-10-01
In the following section, section 6, he says...

6 Configure The Network

Because the Ubuntu installer has configured our system to get its network settings via DHCP, we have to change that now because a server should have a static IP address. Edit /etc/network/interfaces and adjust it to your needs (in this example setup I will use the IP address 192.168.0.100): 

-------

Okay, basic question not covered in the tutorial...

If I'm going to put this server on the Internet (of course), then do I first need to have an Internet address (not 192..) or should the server always go through a router?

It sounds like I'd be using a router with ubuntu server since he references a 192 number.

Since the server would be on a different router, should I first get the internet connectivity and hook up the separate router first?

Thanks again!!!

-- M

---

### Post by hyper_ch on 2007-10-01
192.168.x.x. are private IP addresses. This means they are reserved for LAN (I personally prefer 10.x.x.x --> normally 10.0.0.1 for the router, 10.0.0.3 for my network printer and 10.0.0.5 for my computer).

The settings you have in there are with regard to your connection. If you are behind a router, assign also a static IP address. By default router provide 192.168.0.x...

In the router you should be able to start distributing IP addresses from a certain range (e.g. 192.168.0.100), before that you will then have "static" ip addresses that you can set your server to. E.g. 192.168.0.32

The reason for static IPs are twofold:
(1) if you are on a lan you must know on where to forward ports to... if you run a webserver etc. from within your lan and want it to be accessible from the outside, then your router must know where to forward the ports to. Hence a static IP is required.

(2) mailservers also check if you have a static (public) IP. If not, they may refuse to accept email from you as there are a lot of spam-mailservers that use dynamic ips.

---

### Post by Orbital75 on 2007-10-01
It's very dangerous to put a Server on the same Network (LAN) as your other computers.
I would highly recommend a 2 router (Double NAT) setup. You should also use something
like SmoothWall to do this. The reason I say this is because if a Bad guy compromised your
Server, he now has access to all the computers on your network.

---

### Post by az on 2007-10-01
See this about using LAMP on your home computer:
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by hyper_ch on 2007-10-01
> **Orbital75 said:**
> The reason I say this is because if a Bad guy compromised your
Server, he now has access to all the computers on your network.

It depends on how you setup the network...

---

### Post by msprygada on 2008-01-10
OK, I just did the same. A little background first. We are a Windows 2003 network and have everything we need to operate here. I have two old Compaq Proliant servers laying around that work but have been decommissioned because of age. So what I am looking for are ideas as to what to use this server for. I read where people use Linux servers in a Windows environment, what are people doing with a Linux box in that scenario? 

I installed Ubuntu Server 7.1 on one of them and need some direction as to what its possible uses could be as an addition to our current environment (SAN, etc, etc). I am sure there are things that it can be used for that I do not know about.

Thanks for your ideas in advance...

---

### Post by il-luzhin on 2008-01-11
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)

Maybe this will help.

---

