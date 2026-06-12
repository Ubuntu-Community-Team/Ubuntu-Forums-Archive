---
title: "[SOLVED] Weird ping behaviour"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-13
Hi there,

I have some strange behaviour with ping

if I do
```
ping ubunturocks
```I get a response no matter what hostname I ping. I don't have a machine called ubunturocks.  Here's the response:
```
PING ubunturocks (208.69.32.139) 56(84) bytes of data.
64 bytes from 208.69.32.139: icmp_seq=1 ttl=53 time=117 ms
64 bytes from 208.69.32.139: icmp_seq=2 ttl=53 time=115 ms
64 bytes from 208.69.32.139: icmp_seq=3 ttl=53 time=117 ms
64 bytes from 208.69.32.139: icmp_seq=4 ttl=53 time=116 ms
64 bytes from 208.69.32.139: icmp_seq=5 ttl=53 time=115 ms
64 bytes from 208.69.32.139: icmp_seq=6 ttl=53 time=115 ms
64 bytes from 208.69.32.139: icmp_seq=7 ttl=53 time=117 ms
64 bytes from 208.69.32.139: icmp_seq=8 ttl=53 time=117 ms
64 bytes from 208.69.32.139: icmp_seq=9 ttl=53 time=116 ms
64 bytes from 208.69.32.139: icmp_seq=10 ttl=53 time=117 ms

--- ubunturocks ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9074ms
rtt min/avg/max/mdev = 115.616/116.673/117.406/0.656 ms
```Why is that? I have a Netgear DG834 ADSL Router connected to my Ubuntu server. The only thing that I can think of is that I have added two DNS servers into my router becuase I wanted to use OpenDNS. Is this the issue? The DNS servers I have entered are: 208.67.222.222 and 208.67.220.220.

Thanks for any light. This problem is preventing a lot of network jobs from running because hostnames always get resolved to the OpenDNS servers.

keymoo

---

### Post by bwhitaker on 2007-09-13
Your dns servers are returning an ip for every domain.  This is a process started by networksolutions about 8 years ago so they could attempt to sell you domains that were available.  Many dns servers do it now.

I just did a dig off of one of the servers you listed and this is the response I got:

$ dig @208.67.222.222 adssuck.thisisnotarealdomain.zzzzz

; <<>> DiG 9.3.4 <<>> @208.67.222.222 adssuck.thisisnotarealdomain.zzzzz
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45580
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;adssuck.thisisnotarealdomain.zzzzz. IN A

;; ANSWER SECTION:
adssuck.thisisnotarealdomain.zzzzz. 0 IN A      208.69.32.130

;; Query time: 104 msec
;; SERVER: 208.67.222.222#53(208.67.222.222)
;; WHEN: Thu Sep 13 14:20:07 2007
;; MSG SIZE  rcvd: 68


Of course that is a bad domain, infact .zzzzzz isn't a valid top level domain, however when I browse to that using your dns server it redirects to [http://guide.opendns.com/?url=adssuck.thisisnotarealdomain.zzzzz](http://guide.opendns.com/?url=adssuck.thisisnotarealdomain.zzzzz)  which has a google style search engine in it.  This allows them to generate ad revenue, I'm guessing so that their service will remain free.

I would suggest finding a free normal dns server to use instead, or run your own bind servers with root hints.

---

### Post by bwhitaker on 2007-09-13
I found a link support article that tells why they do this:
[http://www.opendns.com/support/article/14](http://www.opendns.com/support/article/14)

> 
How does OpenDNS make money?

 OpenDNS makes money by offering clearly labeled advertisements alongside organic search results when the domain entered is not valid and not a typo we can fix. OpenDNS will provide additional services on top of its enhanced DNS service, and some of them may cost money. Speedy, reliable DNS will always be free.


---

### Post by keymoo on 2007-09-13
Thanks - I changed my DNS servers back to my ISP's and everything works OK now. Weird.

---

