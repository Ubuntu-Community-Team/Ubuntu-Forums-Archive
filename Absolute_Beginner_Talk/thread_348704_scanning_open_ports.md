---
title: "scanning open ports"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by bcs on 2007-01-29
Hello,
I just realized that I have ports 8180 and 8080 open (for tomcat and oracle, respectively)...It's not a major concern, but I would like to close those two ports.  Is there anyway to close the ports, while keeping those services running on localhost?  Also, is there a tool to check to see what ports are open on my own machine?  (I ran "Port Scan" (under network tools) on localhost, but it didnt come up with ports that I knew were open.  Thanks for the help!

---

### Post by finer recliner on 2007-01-29
nmap is very good

its in the repositories

---

### Post by bcs on 2007-01-29
Thanks, finer recliner! I just got nmaps and it showing my open ports...do you know how I can close them without killing the services on localhost??

---

### Post by The Tronyx on 2007-01-29
> **bcs said:**
> Thanks, finer recliner! I just got nmaps and it showing my open ports...do you know how I can close them without killing the services on localhost??

Do you use a router?  Depending on which type of router try opening firefox and typing 192.168.0.1.  If that doesn't bring up a login prompt for your router consult your manual, though I don't think every router let's you close ports from their administration options. 

Do you use a linux firewall?  If you do you might also want to try and open your firewall program and configure the ports you wish to close from there.

HTH

---

### Post by finer recliner on 2007-01-29
by default, all ports on ubuntu are closed, unless opened by another program. i unfortunately dont know much more than this.

---

### Post by irish_flu on 2007-01-29
BCS- What you're looking for is a "firewall".  The best firewall exists outside of your computer. Many home users have a router with a firewall built-in.  Many businesses will use a Linux computer whose sole purpose is to act as a firewall for their network, passing traffic from the outside to the inside.

With a firewall, you can "listen" on whatever ports you want on your machine, but if the port isn't open on the firewall than nobody "outside" of the firewall can see the open port.

If you don't have the option of using an outside firewall such as a router with a firewall included, then there are some software solutions.

I went to Synaptic and did a search for "firewall".  It found a package in the "Universe" repository called "firestarter".  I've never used it, but it claims to be a "complete firewall tool for Linux machines,  It features and easy to use firewall wizard to quickly create a firewall.".

So, while I've never used the Firestarter package and can't vouch for it, it sounds from the description like it would do what you're asking.

---

### Post by bcs on 2007-01-29
Thanks for the input.  my laptop is behind a router/firewall on my home network (where I do 80% of my work).  WIth this in mind and because of the fact that it is only ports for a web server and oracle server that are open, I don't think it is that much of a big deal from a practical perspective.  As far as the firewall, I thought (but could be wrong) that ubuntu comes standard with a firewall: iptables.  Firestarter is a front-end for iptables that allows you to easily control which ports are open/closed.

---

### Post by irish_flu on 2007-01-29
As far as I know, you're exactly right about iptables and firestarter.  I'd also agree that if your outside firewall is locked down, it's not to big of a deal to worry about closing ports inside it (unless you don't know who's on your inside network, hehe).

---

### Post by bcs on 2007-01-29
I just installed firestarter (basically to see how it works)...now the ports that I mentioned are closed to outside traffic, but I just realized that my machine responds to pings (which I had assumed that it hadn;t)...I tried to stop it from doing this by using firestarter's controls, but can;t seem to get it to stop.  Anyone know how to make my machine stop responding to pings??

---

### Post by finer recliner on 2007-01-30
it is not recommended that turn off normal ping operation, as many other protocols and services rely on it. turning it off will probably lead to weird errors and events.

---

