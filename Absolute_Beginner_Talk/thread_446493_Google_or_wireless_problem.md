---
title: "Google or wireless problem?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by forwhat? on 2007-05-17
I'm new to the ubuntu world. But everything has been working ok till for some reason my google search engine will not work right. When I open Firefox i type in [www.google.com](www.google.com) and press enter but it just seems to be waiting for google to respond.  I try yahoo, msn, and others. they open up with no problem. Also after a wile of being online for some reason i get disconnected, even though the little bars on the top right next to the clock show that I'm connected. then when i put the cursor over the little bars the connection will be around 50% strength. O yeah, I also downloaded Opera to see if it worked there but i had the same result. It all works fine on Windows Xp.
My computer is set up wireless. I have a Linksys WUSB300N wireless-N network adapter.
AMD 3700+ water cooled
ABIT A8N 32X mobo
NVIDIA 6800GS gpu
1G XMS RAM

---

### Post by mills on 2007-05-17
probably just temporary, can you ping it?

```
ping www.google.com
```

---

### Post by forwhat? on 2007-05-17
I did the ping thing. what is it. it just kept going and going like this.
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=215 ttl=242 time=39.9 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=216 ttl=242 time=39.9 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=217 ttl=242 time=40.3 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=218 ttl=242 time=40.0 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=219 ttl=242 time=40.0 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=220 ttl=242 time=40.4 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=221 ttl=242 time=40.6 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=222 ttl=242 time=40.1 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=223 ttl=242 time=40.5 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=224 ttl=242 time=42.1 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=225 ttl=242 time=40.2 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=226 ttl=242 time=40.2 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=227 ttl=242 time=40.3 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=228 ttl=242 time=45.3 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=229 ttl=242 time=42.2 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=230 ttl=242 time=41.4 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=231 ttl=242 time=40.8 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=232 ttl=242 time=40.4 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=233 ttl=242 time=40.8 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=234 ttl=242 time=40.9 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=235 ttl=242 time=38.9 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=236 ttl=242 time=39.0 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=237 ttl=242 time=40.4 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=238 ttl=242 time=38.5 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=239 ttl=242 time=73.7 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=240 ttl=242 time=95.4 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=241 ttl=242 time=39.6 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=242 ttl=242 time=41.2 ms
64 bytes from bf-in-f99.google.com (72.14.209.99): icmp_seq=243 ttl=242 time=40.9

---

### Post by mills on 2007-05-17
iam not a networking expert but i cant see any reason why you cant connect to Google, if you can ping it your browser should be able to connect.

how long has it been like this?

---

### Post by mills on 2007-05-17
try this

it should tell us if its the browser or internet generally

```
ping -c3 www.google.com
```

---

### Post by wormser on 2007-05-17
It could be a DNS issue.  Try putting the ip address from the ping in Firefox.  - 72.14.209.99

If it works then it is a DNS issue.  

System->Administration->Network->DNS

Enter in:
208.67.222.222
208.67.220.220

Let us know if it works.

---

### Post by mills on 2007-05-17
> **wormser said:**
> It could be a DNS issue.  Try putting the ip address from the ping in Firefox.  - 72.14.209.99

If it works then it is a DNS issue.  

System->Administration->Network->DNS

Enter in:
208.67.222.222
208.67.220.220

Let us know if it works.

why didnt i think of that:confused:

---

### Post by wormser on 2007-05-17
> **mills said:**
> why didnt i think of that:confused:

So it worked?

Oops, you were not the one with the issue.

---

### Post by forwhat? on 2007-05-17
i added the DNS # but i still wont connect with google. it just ends up timing out. i also tryed puting the ping in firefox with no luck.

mills i enterd the ping comand and this is what i got
ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (72.14.209.104) 56(84) bytes of data.
64 bytes from bf-in-f104.google.com (72.14.209.104): icmp_seq=1 ttl=242 time=46.5 ms
64 bytes from bf-in-f104.google.com (72.14.209.104): icmp_seq=2 ttl=242 time=46.5 ms
64 bytes from bf-in-f104.google.com (72.14.209.104): icmp_seq=3 ttl=242 time=47.0 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 46.512/46.681/47.004/0.288 ms
silversurfer1@silversurfer1-desktop:~$

---

