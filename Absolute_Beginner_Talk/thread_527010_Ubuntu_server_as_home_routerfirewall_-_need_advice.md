---
title: "Ubuntu server as home router/firewall - need advice"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by barduck on 2007-08-16
Hi all,

I was happily using an old version of ClarkConnect on my home router/firewall box for several years until the HD crashed recently and I need to rebuilt the machine. I don't like the newer free versions of ClarkConnect because of their limitations and build-in "phone home" "features".

I am thinking about Ubuntu server as the base for my new setup and have several questions:

[LIST=1]
[*]Is Ubuntu server suitable for this task? 
[*]Is it considered secure enough out of the box or do I need to perform and special preventive measures on the default installation?
[*]Can anyone recommend a good firewall script? Something with all the basic rules, logs, zones, dynamic IPs etc? Maybe something that can load config files for easy configuration of port forwarding and blocked IPs?
[*]ClarkConnect has a nice network watch script to monitor the network, check if up (check the ppp interface, ping with retries and timeouts) and then restart the connection, the firewall, update the dynamic DNS service etc. Is there anything similar in Ubuntu server or anything recommended I can get elsewhere? 
[/LIST]


(I know that the firewall and net watcher scripts and not that difficult to write but if there is anything already made and debugged, why reinvent the wheel)

Thanks in advance
- barduck

---

### Post by Jimmyfj on 2007-08-16
1: Ubuntu server most suddenly is up to the task. 

2: Ubuntu server is as secure as you want it to be. Out of the box install is very secure. I have run an Ubuntu server, 6.10 for almost a year now and have never set up additional measures of security on it.

3: If the computer is big enough I'd suggest that you set it up with a GUI in order to set up your own security. The use of others security also means that others are able to work around it. Just install a GUI and use firestarter or other utilities. 

4: In a GUI server you can install Wireshark or Etherabe to monitor your network graphically. 

The other features you mention, haven't tried them.

---

### Post by barduck on 2007-08-16
Thanks for the reply Jimmy.

I am using an old PII machine so any GUI is out of the question.

Also, Wireshark is not what I am looking for, it is for inspecting the traffic and I need a script that checks if the ppp link is up, makes sure it is restarted if needed and then restarts/updates all the depending systems.

---

### Post by darksidedude on 2007-08-16
not so, this isnt windows man, there are many guis that work on p2

(fluxbox, xubuntu,.....) and many more!

---

### Post by barduck on 2007-08-16
> **darksidedude said:**
> not so, this isnt windows man, there are many guis that work on p2

(fluxbox, xubuntu,.....) and many more!

Yeah maybe...but this is a router/firewall box, what do I need a GUI for? It just takes resources. 99.9% of the time this box is sitting in a dark corner under the table without mouse/keyboard/monitor attached, only accessed by SSH.

---

### Post by digilink on 2007-08-16
> Yeah maybe...but this is a router/firewall box, what do I need a GUI for? It just takes resources. 99.9% of the time this box is sitting in a dark corner under the table without mouse/keyboard/monitor attached, only accessed by SSH.

Agreed. Having X on a server that is doing nothing but firewall duties is a serious waste of resources. 

Personally, I use Smoothwall for my firewall duties nowadays, I had a dedicated Debian box I was using for a while, but I find that Smoothwall more than fills my needs and it's just another box I don't have to manage. 

You could always use Firewall Builder [http://www.fwbuilder.org/](http://www.fwbuilder.org/), this is a GUI based program you can run on another machine, build your specs, and it will create and apply the iptables rules for you. I've used it in the past with a lot of success, YMMV however.......

---

