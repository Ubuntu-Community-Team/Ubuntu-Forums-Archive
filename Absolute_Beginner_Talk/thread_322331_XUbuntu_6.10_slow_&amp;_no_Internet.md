---
title: "XUbuntu 6.10 slow &amp; no Internet"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2006-12-20
Hello,

Yesterday I installed XUbuntu 6.10.  At first glance it's excellent and I'm hoping to continue using it.  I have however, two problems.  

1) Applications (even command-line ones such as vim) start very slowly.
2) Internet is inaccessible (sort of).
       I can download updates using Update Manager and install packages using Synaptic.  I can ping a server such as Google, but when I try to view it using Firefox the connection times-out.  Oddly I can access Ubuntu web pages, albeit slow.  When I boot to Windoze (I thought I'd never have to do it again since I made the smart choice to switch to Linux) my Internet works fine.  I've had Mepis prior to installing XUbuntu and Mandriva before that, and XandrOS before that and all worked fine.    

I have plenty of memory and processing power.  

I configured my Internet connection for DHCP and XUbuntu recognizes it.  When I use pppoeconf I get an error that my ISP's Access Concentrator is not found.  

My ADSL router is a StarBridge Lynx 210.  

Please help.  Thank you.

---

### Post by ashrack on 2006-12-20
> **x1a4 said:**
> Hello,

Yesterday I installed XUbuntu 6.10.  At first glance it's excellent and I'm hoping to continue using it.  I have however, two problems.  

1) Applications (even command-line ones such as vim) start very slowly.
are U using a laptop?
give us the info from:
```
cat /proc/cpu
```

> 2) Internet is inaccessible (sort of).
       I can download updates using Update Manager and install packages using Synaptic.  I can ping a server such as Google, but when I try to view it using Firefox the connection times-out.  Oddly I can access Ubuntu web pages, albeit slow.  When I boot to Windoze (I thought I'd never have to do it again since I made the smart choice to switch to Linux) my Internet works fine.  I've had Mepis prior to installing XUbuntu and Mandriva before that, and XandrOS before that and all worked fine.    
try this:
[http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6](http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6)

> I have plenty of memory and processing power.  
tell us the specs.

> I configured my Internet connection for DHCP and XUbuntu recognizes it.  When I use pppoeconf I get an error that my ISP's Access Concentrator is not found.  

My ADSL router is a StarBridge Lynx 210.  

Please help.  Thank you.
pppoeconf and DHCP are to seperate things.
uf U have a ruter than U are almost certantly using DHCP.
If U have a ADSL modem which require PPPOE deamon for it to work than that is a hole other thing. 
What do U have, check with your ISP if not sure...

---

### Post by x1a4 on 2006-12-20
> **ashrack said:**
> are U using a laptop?
No

> give us the info from:
```
cat /proc/cpu
```
cat: /proc/cpu: No such file or directory
 
> try this:
[http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6](http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6)


> tell us the specs.
AMD Sempron 2400 & 768MB RAM


> pppoeconf and DHCP are to seperate things.
uf U have a ruter than U are almost certantly using DHCP.
If U have a ADSL modem which require PPPOE deamon for it to work than that is a hole other thing. 
What do U have, check with your ISP if not sure...

StarBridge Lynx 210 ADSL ethernet router.

---

### Post by user007usa on 2006-12-20
To test, try using Mozilla or Opera to see if it works.  Does it?

Try typing "about:config" in the url window then find the value: network.dns.disableIPv6 and right click on it and choose toggle to make it say true.  Then restart firefox.

---

### Post by x1a4 on 2006-12-20
Eureka!

ashrack, I followed the instructions in the post you provided the link to and added the file 
/etc/modprobe.d/bad_list containing the line 'alias net-pf-10 off', rebooted and it works perfectly.  

Thank You  :biggrin:

---

### Post by ashrack on 2006-12-21
no problemo!

---

### Post by LookTJ on 2006-12-21
Tell us the output of

```
cat /proc/cpuinfo
```

Edit: Argh! How do I delete this post?

---

