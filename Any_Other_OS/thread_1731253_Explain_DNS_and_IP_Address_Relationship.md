---
title: "Explain DNS and IP Address Relationship?"
date: 2011-04-16
forum: Any Other OS
---

### Post by earthpigg on 2011-04-16
Not so much an Operating System, but an Internet System question.

I always thought that [www.humanwords.com](www.humanwords.com) was mapped to an IP address on the back-end, but never the other way around as it would serve no purpose.

example:
[http://www.google.com](http://www.google.com) may you to [http://74.125.224.84](http://74.125.224.84) (or your local mirror) on the back-end, but it still shows [www.google.com](www.google.com) as a human convenience.
by contrast,
[http://74.125.224.84](http://74.125.224.84) takes you to [http://74.125.224.84](http://74.125.224.84), and **not** to [http://www.google.com](http://www.google.com)

however, something in current events is creating confusion for me.


[http://77.87.179.116](http://77.87.179.116) (physically located in the UK) takes you to [http://www.pokerstars.com/](http://www.pokerstars.com/)

and

[http://91.211.98.20](http://91.211.98.20) (physically located in Ireland) takes you to [http://www.fulltiltpoker.com/](http://www.fulltiltpoker.com/)

True when using OpenDNS, as well.

When I ping them both, in the example of fulltitlt:

```
[chris: ~]$ ping -c 3 91.211.98.20
PING 91.211.98.20 (91.211.98.20) 56(84) bytes of data.
64 bytes from 91.211.98.20: icmp_req=1 ttl=236 time=172 ms
64 bytes from 91.211.98.20: icmp_req=2 ttl=236 time=182 ms
64 bytes from 91.211.98.20: icmp_req=3 ttl=236 time=172 ms

--- 91.211.98.20 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 172.386/175.710/182.155/4.583 ms
[chris: ~]$ ping -c 3 www.fulltiltpoker.com
PING www.fulltiltpoker.com (50.17.223.71) 56(84) bytes of data.

--- www.fulltiltpoker.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

[chris: ~]$ 
```



How did this come to pass? Does this imply that folks in the UK and Ireland have gotten involved, or that my understanding is off?


Note that I am not seeking to violate any laws of any relevant jurisdiction - I've never done the online gambling thing, and I'm pretty sure nothing discussed in this thread would cause either of the websites to magically re-appear for me or anyone else. 

I would like my (mis)understanding of the DNS system clarified, though.

---

### Post by earthpigg on 2011-04-16
ok, maybe this is some progress

[http://91.211.98.20/banner7.jpg](http://91.211.98.20/banner7.jpg)

implying that control of the server itself has been handed over?

---

### Post by rockaroundtheclock on 2011-04-18
When you visit a site you can be redirected wherever they want to redirect you. Like for example ubuntuforums.org:
```
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
```If you put [http://91.189.94.12](http://91.189.94.12) in the browser it sends you to [http://www.canonical.com]("http://canonical.com").

Is that what you're talking about?

---

