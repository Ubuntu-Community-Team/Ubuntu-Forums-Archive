---
title: "firefox really slow"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by bplus on 2006-10-30
Hi,
I ve got a dual boot set up on my laptop with ubuntu 64 and winxp.
I ve just come back to using ubuntu after a few months and I ve noticed that firefox is really badly slow compared to winxp.

Everytime i enter a web address or click on a link it takes ages and says "looking up www.insert_web_address_here.com" eventually the pages do load but this doesnt happen on my windows install at all.

At first I thought it was my wi fi card acting up (ubuntu installed it automatically unlike windows:)  ) but then I tried it with plain old ether net cable and had the same problem.

any idea whats wrong?

I pinged my router and get this time 
> 
bbyrne@Brian-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=128 time=1.30 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=128 time=1.31 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=128 time=1.29 ms


is that a slow response?

---

### Post by happy-and-lost on 2006-10-30
> jo@jo-laptop:~$ ping 86.139.141.95
PING 86.139.141.95 (86.139.141.95) 56(84) bytes of data.
64 bytes from 86.139.141.95: icmp_seq=1 ttl=64 time=2.03 ms
64 bytes from 86.139.141.95: icmp_seq=2 ttl=64 time=1.44 ms
64 bytes from 86.139.141.95: icmp_seq=3 ttl=64 time=1.43 ms


Nope. That's a normal response. Have you tried reinstalling Firefox?
Do you have any extensions installed?

---

### Post by bplus on 2006-10-30
got google browser sync installed.
actually i might aswell upgrade to firefox 2...

---

### Post by bplus on 2006-10-30
well i noticed when I ran
apt-get update
it took about 7 seconds to connect to each server
but when it did the download speed was fine.

this seems to be exactly whats happening to firefox

any ideas, does my router not like ubuntu?

---

### Post by furiousV on 2006-10-30
Have you tried disabling IPv6 in Firefox?

In address bar, go to **about:config**

find **network.dns.disableIPv6** and set to **true**

I hope that helps

---

### Post by IYY on 2006-10-30
What furiousV said.

---

### Post by bplus on 2006-10-31
tried what you said still getting same problem though.
wierdly once i ve connected to site surfing that site is fast, no 
"looking up www.site.com" wait.

This is really odd and it just doesnt happen on my windows xp install](*,)

---

### Post by mahy on 2006-10-31
> **bplus said:**
> tried what you said still getting same problem though.
wierdly once i ve connected to site surfing that site is fast, no 
"looking up www.site.com" wait.

This is really odd and it just doesnt happen on my windows xp install](*,)

How about trying out different browsers to compare the performance? I'd suggest Opera. ;)

---

### Post by jesseakc on 2006-11-05
I had the same problem and found an easy fix.  Get Swiftfox [http://getswiftfox.com/](http://getswiftfox.com/) [Swiftfox]("http://getswiftfox.com").

I have been trying to get my wife to start using an OS besides Windows and Ubuntu seemed to be the solution, however the Internet was increadably slow.  So slow that she even complained about it.  Now that we have Swiftfox, its just as fast if not faster then Windows.

> Swiftfox is an optimized build of Mozilla Firefox. Swiftfox has builds for both AMD and Intel processors. The 2.0 release is based on Firefox 2.0.

It even comes with an easy installer and deb files.

EDIT:  I found out a little more.  I guess that the problem is with something called Pango.  If you don't want to try Swiftfox, I would give this a shot.  I haven't tried this method but it looks pretty good.  Add the line:

MOZ_DISABLE_PANGO=1

in 

/etc/environment

I found this information at  [http://bitubique.com/content/view/43/52/](http://bitubique.com/content/view/43/52/)

Hope this helps.
Jesse

---

### Post by redmarshall on 2006-11-07
MOZ_DISABLE_PANGO=1 Works like a charm.  boosted my speed to a peek

---

### Post by eXume on 2006-11-15
I am experiencing the same. To me it seems it is nothing to do with firefox as i experience the wait in terminal when downloading things as well. Its almost as if it takes a while to connect remotely through the internet connection.
I have no idea why as im a n00b to linux based OS

---

### Post by bikeboy on 2006-11-15
This applies to the OP (last post was a while ago) and you eXume, I think it might be a dns issue.

I'm not in gnome right now so OTOH go to System > Admin > Networking and go to DNS. Put in your isp's dns server addresses and see if that makes a difference.

---

### Post by 16777216 on 2007-02-08
I'm sorry I don't know what the problem is of how to fix it but it seems that everyone thinks you need a new browser, but that is not the case.

This is what I got on a local ping command 

```
$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.402 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.407 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.405 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.406 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.522 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=0.408 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=0.407 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=0.406 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=0.409 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=0.404 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=255 time=0.418 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=255 time=0.404 ms
64 bytes from 192.168.1.1: icmp_seq=13 ttl=255 time=0.458 ms
64 bytes from 192.168.1.1: icmp_seq=14 ttl=255 time=0.404 ms
64 bytes from 192.168.1.1: icmp_seq=15 ttl=255 time=0.441 ms
64 bytes from 192.168.1.1: icmp_seq=16 ttl=255 time=0.395 ms
64 bytes from 192.168.1.1: icmp_seq=17 ttl=255 time=0.401 ms
64 bytes from 192.168.1.1: icmp_seq=18 ttl=255 time=0.414 ms
64 bytes from 192.168.1.1: icmp_seq=19 ttl=255 time=0.416 ms
64 bytes from 192.168.1.1: icmp_seq=20 ttl=255 time=0.417 ms
64 bytes from 192.168.1.1: icmp_seq=21 ttl=255 time=0.401 ms
64 bytes from 192.168.1.1: icmp_seq=22 ttl=255 time=0.403 ms

--- 192.168.1.1 ping statistics ---
22 packets transmitted, 22 received, 0% packet loss, time 21036ms
rtt min/avg/max/mdev = 0.395/0.415/0.522/0.037 ms
```

Again sorry I couldn't help.

---

