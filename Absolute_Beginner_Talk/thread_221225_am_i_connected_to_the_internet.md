---
title: "am i connected to the internet?"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by feelexit on 2006-07-22
New B question.

I got ubuntu server installed.  this one has no gui interface. I  only build it to test my php code.

now, I need to know if my server connected to the internet. there's no browser, i cannot just surf a page to find out.

is there another way to test it ?

---

### Post by agurk on 2006-07-22
ping google.com

---

### Post by Ben Armston on 2006-07-22
Type the following command:

```
 ping -c 3 www.google.com
```

If you are connected to the internet you should get something similar to:

```
PING www.l.google.com (216.239.59.147) 56(84) bytes of data.
64 bytes from 216.239.59.147: icmp_seq=1 ttl=247 time=32.2 ms
64 bytes from 216.239.59.147: icmp_seq=2 ttl=247 time=31.2 ms
64 bytes from 216.239.59.147: icmp_seq=3 ttl=247 time=30.5 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 16209ms
rtt min/avg/max/mdev = 30.575/31.374/32.296/0.707 ms
```

The important bits being on the last but one line: 3 packets transmitted, 3 received. Oh and there are webbrowsers that work on the command line: lynx, links and elinks.

---

### Post by jpkotta on 2006-07-22
```
ping google.com
``` or a different site if you don't like Google.  You can also get text mode browsers, like links, to test without installing X. ```
sudo apt-getr install links
```

---

