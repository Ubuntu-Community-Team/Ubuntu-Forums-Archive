---
title: "Random web page hangups"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-06-14
90% of the time I can browse the internet no problem. Every now and then, when I go to load a page it will say looking up (insert page)... and will never connect. Aa quick restart or even logging in and out solves this. Any ideas what is happening? No problem with windows and I am using a static IP behind a Linksys router. Wired connection as well.

---

### Post by Inxsible on 2007-06-14
> **jba6511 said:**
> 90% of the time I can browse the internet no problem. Every now and then, when I go to load a page it will say looking up (insert page)... and will never connect. Aa quick restart or even logging in and out solves this. Any ideas what is happening? No problem with windows and I am using a static IP behind a Linksys router. Wired connection as well.

Does it simply go darker ? You should wait it out in that case, it will eventually come back. Does restarting the broswer help?

---

### Post by jba6511 on 2007-06-14
no I have seen this happen where it goes dark but returns, but not with my browser. Closing and restarting does not seem to help. Like I said it only happens every now and then, mainly when my computer has been running for awhile. Restarting fixes the problem.

---

### Post by Inxsible on 2007-06-14
> **jba6511 said:**
> no I have seen this happen where it goes dark but returns, but not with my browser. Closing and restarting does not seem to help. Like I said it only happens every now and then, mainly when my computer has been running for awhile. Restarting fixes the problem.

Does everything freeze and you have to do a hard reset or just the browser ?

---

### Post by jba6511 on 2007-06-15
just the browser. I am not sure if it freezing or not since it just gets stuck at Loading .... I can close out and minimize just fine when this happens.

---

### Post by jba6511 on 2007-06-15
screenshot of whats happening.

---

### Post by Rocket2DMn on 2007-06-15
Are you running the latest version of firefox?
Assuming so, have you considered just reinstalling the package?

---

### Post by bone43 on 2007-06-15
> **jba6511 said:**
> 90% of the time I can browse the internet no problem. Every now and then, when I go to load a page it will say looking up (insert page)... and will never connect. Aa quick restart or even logging in and out solves this. Any ideas what is happening? No problem with windows and I am using a static IP behind a Linksys router. Wired connection as well.

It may also be a connections issue with your isp" if possible test you connection with another computer or OS and see if you get the same time outs.

 Also try another browser and see if you get the same problem.

---

### Post by Cappy on 2007-06-16
I'm an editor for newzbin =P

This sounds like this may be a problem with your DNS. I would try turning off DHCP and manually setting up a static IP with your router. You may want to try your secondary DNS.

When this problem happens paste the output from
```
dig sitename.com
```

---

### Post by jba6511 on 2007-06-16
I have dhcp turned off and a static ip set. I will try another browser as well. Any recommendations? It is starting to happen more frequently. I nticed on my laptop ever now and again I will get disconnected from the network, even with a strong signal, but once it reconnects it is fine. I am wondering if it is my ISP. I will post the output from running dig site-name next time it happens.

---

### Post by Austin_KW on 2007-06-16
Disable IPV6, can cause dns problems.

Try a different DNS server (opendns instead of your ISP)

---

### Post by jba6511 on 2007-06-16
can you walk me through disabling IPV6

---

### Post by Austin_KW on 2007-06-16
to disable ipv6 enter the following command in a terminal
 gksudo gedit /etc/modprobe.d/aliases

and change the ipv6 line to;
alias net-pf-10 off #ipv6

---

### Post by jba6511 on 2007-06-17
thanks, i will give this a try and see if it happens anymore.

---

### Post by jba6511 on 2007-06-17
can someone give me another dns server address to try. Even with IPV6 disabled this happened again.

---

### Post by Austin_KW on 2007-06-17
opendns.com
      208.67.222.222
      208.67.220.220

---

### Post by jba6511 on 2007-06-19
well it happened again. I have disabled IPV6 and am using opendns and still having troubles. Any other ideas?

---

### Post by jba6511 on 2007-06-21
happened once again today. This time I tried to do some updates before I noticed the problem and synaptic could not connect to download, so I do not think it is the browser. Any ideas?

---

### Post by jba6511 on 2007-06-24
keeps happening..anyone???? help???

---

### Post by jba6511 on 2007-06-30
well I reset the router to defaults and then reconfigured to see if that helps. Internet is faster loading pages but did not fix the problem. Still unresolved, any ideas???

---

### Post by jba6511 on 2007-06-30
blacklisted ipv6, disabled ipv6, reinstalled firefox, tried opera, nothing...anyone

---

