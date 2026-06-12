---
title: "apache2, openssh, ddclient, dyndns"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by ctrlcctrlv on 2006-11-07
hello all.

I am trying to 

A: run an Apache2 server and 
B: connect remotly to my computer through ssh

It went like this:

LAst night my Apache2 server was running, really simple, takes about 60 seconds. I forwarded 80/443 through my linksys router.ok. People could view my page by my ip address. THats what i wanted.

I set up firestarter and set it to open port 80/ 22(22 might be a security risk i dunno). I install Openssh. ssh client works, I can connect to various remote computers(i know it sounds great and it is). No problems.

I want an ssh server, so start an account with dsndns.org. I installed and configured ddclient. A tutorial instructed me to use port 443 to run my ssh server. I did that. ([http://doc.gwos.org/index.php/Sshlogin](http://doc.gwos.org/index.php/Sshlogin))

I can not for the life of me get my ssh server to work.
For some reason, after i installed ddclient and set up the dynDNS account
My ip adress is somehow blocked, and i can only use localhost to view my web page. I tried uninstalling my firewall. Its not the issue.

How is my dynDNS account related to my Apache2 service on port 80?
Is there a better resource on how to set up an ssh server?
Am I in the wrong forum? 
:)


](*,)

---

### Post by malmjako on 2006-11-07
Have you tried accessing it from outside of your LAN, i.e. from the other side of your router? With a router I had I couldn't access my computer from inside my LAN using the dyndns host name. From the outside this was no problem. (I actually added the dyndns host name to /etc/hosts, so I could use the same address as from the outside. Don't know if there would be any unwanted effects from doing that...)

And then, maybe I completely misunderstood your problem...

---

### Post by ctrlcctrlv on 2006-11-07
I actually formatted and reinstalled again. 

I reinstalled Apache2. I can not access my page from inside my LAN as you suggested. How ever I ahve not tried it form outside. On the other hand, since I renstalled all those config files should be gone. It is my impression that dynDNS is for ssh traffic. I think im not clueing in on something fundemental here. 
I just need to have a working server :)

this is getting silly

paul

---

