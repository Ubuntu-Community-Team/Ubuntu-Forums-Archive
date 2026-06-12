---
title: "cannot get onto internet - sort of"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Carolyn62 on 2006-11-12
Hi,
I am an absolute beginner and am determined to become independent of windows. I maybe an older lady but I'll be darned if I am going to allow Bill you who keep me from using Linux.

With that said I installed Ubuntu 6.06LT finally without a hitch. I was even able to get onto the internet using fire fox. I installed updates for Ubuntu with no problem, then all of a sudden after I went out of 6.06 to XP, then coming back it's almost as if I have a half of an internet connection.

I can get to some of the areas such as Mozilla and Ubuntu forums but that's it. It won't accept Google searches or download programs, or updates for Ubuntu.

I went to systems, network, and ethr0 (I think I spelled it right) and it is set to DHCP with the correct DNS servers (192.168.0.1 and 205.171.3.65) which matches up with XP (i had learned how to find it by searching the forums).

I do not know what else to do as I learned a long time ago that throwing a tantrum won't help, but I am so new at this I may do it anyway to keep from crying (just kidding). Is there anyone who can help step me through this? I even tried following the Ubuntu book that I downloaded from the internet with no success. I have no password or login name because I signed up for quest basic as I did not need or want MS as an IP

Thank You,
Carolyn

---

### Post by DaveBorealis on 2006-11-12
> **Carolyn62 said:**
> I can get to some of the areas such as Mozilla and Ubuntu forums but that's it. It won't accept Google searches or download programs, or updates for Ubuntu.

Hello Carolyn,

I'm a little confused about your problem.  You can get out onto the internet to some sites, but not to others?  Go to 'Applications->Accessories->Terminal' and type in:
```
ping -c1 www.google.com
ping -c1 64.233.167.99

```

And post back here what you get.  It'll perhaps help to narrow down your problem.

Dave

---

### Post by autocrosser on 2006-11-12
As I am on Dialup, I can't give you exact pointers---but I would start by looking at:  [https://help.ubuntu.com/community/InternetHowto](https://help.ubuntu.com/community/InternetHowto)   (if you can nav to the page;))

This might also shed some light on your problem:

**Error logs**

  If you are having problems with your connection, you may find valuable information in the system message logs. You may acces system logs either in a terminal, or with a graphical interface. 
 [LIST]
[*] To use the grapical log viewer, in the menu bar, go to : System > Administration > System Log. You will find the system messages in /var/log/messages. 
[*] To use the terminal, type:  
[/LIST]  sudo dmesg

Hope this helps!!

---

### Post by Carolyn62 on 2006-11-12
OK, here's the result from the pings:

--- [www.google.com](www.google.com) ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 49.251/49.251/49.251/0.000 ms
swrcar@tux:~$ ping -c1 64.233.167.99
PING 64.233.167.99 (64.233.167.99) 56(84) bytes of data.
64 bytes from 64.233.167.99: icmp_seq=1 ttl=245 time=84.7 ms

--- 64.233.167.99 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 84.762/84.762/84.762/0.000 ms


Even if I do not know Ubuntu I can tell that there is a connection of some sort.

So I decided to go to Firefox and try to reply from dapper.
Well I can tell you that I can cook a steak faster then this browser is. For each click of the mouse (forums, beginners, etc) it takes between 4 and 7 minutes for any kind of action. The bar in the browser moves about 3/4's of the way then sits there for those 4-7 minutes (that for EACH click of the mouse.)

When I type in goggle.com it, the browser time out.

I am going to go back to XP to see what you would have me do next. It will be faster if I go back and forth.

Carolyn

P.S.
Thank you

---

### Post by DaveBorealis on 2006-11-12
> **Carolyn62 said:**
> Even if I do not know Ubuntu I can tell that there is a connection of some sort.

Yep, you've got a connection.  The problem lies elsewhere.  But the question is what's slowing down your computer to such a crawl when you go online.  I'm assuming that other things work at normal speed; it's only the internet/Firefox that's acting so slow?

What kind of memory and CPU speed does your computer have?

Dave

---

### Post by Carolyn62 on 2006-11-12
pent. 3, 866, 512 memory.

everything works fast except the internet, including loading and unloading.

I hope you don't want me to reinstall FF because I am not sure how to do it using add/remove.

Carolyn

---

### Post by Daveski on 2006-11-12
Hi there. I had a very slow firefox until I dicovered turning off IPv6 support. This sorted my long waits in firefox.
See the section on Mozilla in this link:
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by teaker1s on 2006-11-12
I've had a similar issue with dapper and edgy-it turns out that that certain hardware combinations don't work-are you using a router/ if so manually configure static ip and dns.

also worth a look at ipv6 issues-search forums

finally I'm running on broadcom wireless and found that certain apps don't work with my hardware-if there is a suitable alternative then try it

---

### Post by DaveBorealis on 2006-11-12
> **Carolyn62 said:**
> I hope you don't want me to reinstall FF because I am not sure how to do it using add/remove.

I'm baffled (and hoping someone who knows what's going on steps in here), but I don't think it's a problem with Firefox.  Something's throttling down your connection.  But what?  iptables?  (Have you set up a firewall using something like firestarter?)

---

### Post by Carolyn62 on 2006-11-12
Hi,

> Hi there. I had a very slow firefox until I dicovered turning off IPv6 support. This sorted my long waits in firefox.
See the section on Mozilla in this link:
[https://help.ubuntu.com/community/We...ngSlowIPv6IPv4](https://help.ubuntu.com/community/We...ngSlowIPv6IPv4)

I printed this out and will try it next...Thank You

> I've had a similar issue with dapper and edgy-it turns out that that certain hardware combinations don't work-are you using a router/ if so manually configure static ip and dns..

I am using ethernet (ADSL)

> (Have you set up a firewall using something like firestarter?)

No, no firewalls. I did install Mozilla to see what would happen and got the same thing. Some sites in the bookmark sections worked like lighting and others took forever.

Because of the wnd and rain we are having in the northwest I may not be able to do this until tomorrow but I will try.

I wish to thank all of you for trying to help and will let you know.

Carolyn

---

### Post by Carolyn62 on 2006-11-12
:) :) :) Hello :D :D :D 

Problem solved!!!! Thank you teaker1s, it works perfectly now.

Dave, Thank you so much for the help. I am writing this from dapper even as we speak and this is a very fast connection.

Again, thanks to all of you.

Carolyn

---

