---
title: "Can't connect to internet through router"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by marcfell27 on 2008-02-23
Hi

My setup 

Laptop (toshiba satelitte) connecting through netcomm v300 router (voip) into siemens speedstream modem 

Fresh install of Gutsy - I can ping [www.google.com](www.google.com) and the router 192.168.30.1 and the modem 10.0.0.138 perfectly, but firefox won't connect... the laptop has the ip 192.168.30.3 / 192.168.30.2 is my PC which has XP and connects to the net through browser no problem>...

When I plug the laptop directly to the modem firefox connects to the net.

What's going on.....

I've searched a few posts and I''ve disable IPV6 in about:config which did nothing...  also i did the following from another post also with no avail.
##########################################
Do a &#8220;sudo gedit /etc/modprobe.d/aliases&#8221;
from a terminal window.
Add the following line, and comment out the line that is commented out below:
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6
##########################################

I've also installed epiphany browser and no good either...

Any help  greatly appreciated

---

### Post by dcstar on 2008-02-23
> **marcfell27 said:**
> Hi

My setup 

Laptop (toshiba satelitte) connecting through netcomm v300 router (voip) into siemens speedstream modem 

Fresh install of Gutsy - I can ping [www.google.com](www.google.com) and the router 192.168.30.1 and the modem 10.0.0.138 perfectly, but firefox won't connect... the laptop has the ip 192.168.30.3 / 192.168.30.2 is my PC which has XP and connects to the net through browser no problem>...

When I plug the laptop directly to the modem firefox connects to the net.

What's going on.....

I've searched a few posts and I''ve disable IPV6 in about:config which did nothing...  also i did the following from another post also with no avail.
##########################################
Do a “sudo gedit /etc/modprobe.d/aliases”
from a terminal window.
Add the following line, and comment out the line that is commented out below:
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6
##########################################

I've also installed epiphany browser and no good either...

Any help  greatly appreciated

Install tcptraceroute and do a port 80 trace.

---

### Post by marcfell27 on 2008-02-24
> **dcstar said:**
> Install tcptraceroute and do a port 80 trace.

thanks for your reply,

I've installed tcptraceroute,

what is the code in the terminal to do the port 80 trace??? 

thanks in advance

---

### Post by kaginken on 2008-02-24
I'm pretty sure it's just

```
tcptraceroute www.google.com
```

or whatever internet site you want to hit.  This should start timing out at your routers IP if it is indeed your router blocking port 80.  Post the output for us.

---

### Post by marcfell27 on 2008-02-25
no it's not blocking port 80 as it goes, hard for me to post results as the machine is my father in laws at his house, i'm going around next weekend to **FIX** the problem and get him using this great new OS called ubuntu that I've been raving about to him....  

I might have to reinstall windoz (shreak) if i can't solve this little folly...

please keep this post in mind when your not doing anything next weekend....

---

