---
title: "problems with port forwarding"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by maxding on 2007-02-24
I've setup my apache2 web server and purchased a domain.  I've made my server have a static ip assigned by a netgear wgr614 router.  I've setup port forwarding on my router.  Yet i cannot get to my site, [http://www.mdinges.info](http://www.mdinges.info) from outside.  I can ping the site which does ping my ip address assigned by ISP which is [http://65.191.33.31](http://65.191.33.31) ive been playing with the settings in the router all day and nothing.  I can port forward, port trigger and use a DMZ server setting, but none of it works.  I think maybe i'm being blocked on port 80 but i went to [www.canyouseeme.org](www.canyouseeme.org) (or somthing close) and it said my port 80 wasn't blocked.  I'm getting confused because i am very very new to linux, ubunut, and apache and working in the terminal has been an experience for me.  Anyone with advise please help me.  

thanks

max

---

### Post by nonewmsgs on 2007-02-24
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
will make sure that that port is open

---

### Post by maxding on 2007-02-24
my ip just changed sorry ive been messing with my router.

it's 65.191.182.28

---

### Post by maxding on 2007-02-25
it tells me 
# Sudo: illegal option `-A'

---

### Post by maxding on 2007-02-25
i entered that line of code (correctly) and i got not msg just went to another prompt and i still cannot connect to my server from outside of my lan.  

site [www.mdinges.info](www.mdinges.info) on ip 65.191.182.28

---

### Post by Gordy on 2007-02-25
Do you have a static ip or are you recieving DHCP from youe ISP?

If you are recieving DHCP try using no-ip.com. I use Apache Server with DHCP and am using no-ip.com as a Dynamic DNS service. It is free and works great!

---

### Post by maxding on 2007-02-25
i am dhcp but up until today my router has changed IP's in months

---

### Post by undertakingyou on 2007-02-25
Gordy,

that no-ip.com looks really cool.  I think I'll have to use that for some of my own stuff.

On the subject though, there is a huge possibility that because of changes in your IP from your ISP and not being on any DNS servers that no one can get to you.  Also, is the forwarding in your router set up for both directions?

---

### Post by maxding on 2007-02-25
i would assume so i don;t much about the router.  i setup port forwarding for http on port to a static ip i created in the router and set the server on.  I can get into the server on my lan just not through a wan.

---

### Post by undertakingyou on 2007-02-25
Do you have any firewall up that might prevent any IP range from getting to that server?  If not your right it really would have to be in the router.  Are we sure that all requests come in on port 80?  Does apache listen to any other ports.  I have an apache server I set up at work but I don't know if it uses other ports. . .   I might look into that.

---

### Post by maxding on 2007-02-25
i'm on ubuntu with no firewall my router has a firewall that is disabled.  im pretty sure all the requests are coming in port 80, however, if they do not the router is only setup to forward to and from port 80.  As far as i know thats about all i can do unless it is in my appache.conf or my 000-default which i am clueless as to how to use for the most part.

max

---

### Post by maxding on 2007-02-25
somehow i set it up to access my router online... maybe this means im getting closer.... i hope

---

### Post by undertakingyou on 2007-02-25
Well, I just checked the one apache server I've got, and the httpd.conf file had it set to listen to port 80, so that should be the one.  

In you router, you have port forwarding set, does it have a certain range set? So only a certain IP address will be forwarded.  The wierd thing is that port 80 is almost universally defaulted to forward.

---

### Post by maxding on 2007-02-25
its setup in the router correctly i think.  until i made my domain connect with my router.. my computer tries to connect with the server it timesout something is trying to happen.

---

### Post by Gordy on 2007-03-30
> **undertakingyou said:**
> Gordy,

that no-ip.com looks really cool.  I think I'll have to use that for some of my own stuff.

On the subject though, there is a huge possibility that because of changes in your IP from your ISP and not being on any DNS servers that no one can get to you.  Also, is the forwarding in your router set up for both directions?

I have never had any problems with my ISP at all. no-ip has worked without any hitch and is very very reliable.. Port forwarding on the router is easy to setup and again, I have had no problems. My IP changes often from my IPS servers however, all works all the time. I have been doing this for about 7 months now... It just works right all the time.

---

