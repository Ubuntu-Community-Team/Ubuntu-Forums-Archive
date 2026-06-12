---
title: "Fresh Install, Installed Apache2, my ip is blocked"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by ctrlcctrlv on 2006-11-07
Since I registered with dynDNS I have been unable to access my web page 
by my own ip address. Up until now I have been able to type my ip address
into my browser and access my page.

THis is a fresh install of Dapper.

Is this supposed to be happening?


thx

paul

---

### Post by darth_vector on 2006-11-07
DNS is only used to resolve the domain name. You would be able to access a webserver by IP - if it is up and running - even if the DNS system is down.

i would suggest testing your webserver and firewall to make sure they are up and not being blocked.

---

### Post by ctrlcctrlv on 2006-11-07
ok,

there is no fire wall, i havent installed it

the only thing that is different from when it was working just fine yesterday is that i registered with dynDNS. but none of my config files know about that because i flushed the system.

I registered with dynDNS last night to set up a ssh server with ddclient as instructed by most tutorials and my freind who run Ubuntiu. now my ip is blocked. I basically installed Ubuntu, then I installed apache.

this is really frustrating sigh...

---

### Post by ctrlcctrlv on 2006-11-07
thanks anyways

---

### Post by sbassett on 2006-11-07
If you have installed apache, you might want to try opening port 80. I believe that Ubuntu blocks access by default. You can do this one of two ways, 

1. Install firestarter, a graphical firewall manager.

2. Add an iptables rule.
   From a terminal
    ```
sudo /sbin/iptables -I INPUT -p tcp --destination-port 80 -j ACCEPT 
```

   This will open port 80, also remember to take care of any port forwarding if you are behind a router.

The above line should be inserted within /etc/rc.local to have this port opened at every boot-up.

---

