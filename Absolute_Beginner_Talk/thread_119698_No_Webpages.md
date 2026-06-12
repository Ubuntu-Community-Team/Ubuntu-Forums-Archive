---
title: "No Webpages"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-01-20
I have been working on getting my modem to work for about a week.

Now that I have it working and it connects to my isp perfectly another problem arises.

Everytime I try and go to any where it says that the website's server was not found.

I checked the dial up connection box and I have very little coming in but it is coming in like an idle connection.

Anyone have an Idea of what I can do to go places online?

---

### Post by crovax666 on 2006-01-20
Just a guess, it might be that you don't have any DNS servers registered in /etc/resolv.conf

If it says something like "hostname not found" or something like it.... its that.

Try the following things in a console window

ping -c 1 google.com
ping -c 1 72.14.207.99

I get the output below, my output:
```

/etc$ ping -c 1 google.com
PING google.com (64.233.187.99) 56(84) bytes of data.
64 bytes from 64.233.187.99: icmp_seq=1 ttl=237 time=104 ms

--- google.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 104.163/104.163/104.163/0.000 ms

/etc$ ping -c 1 72.14.207.99
PING 72.14.207.99 (72.14.207.99) 56(84) bytes of data.
64 bytes from 72.14.207.99: icmp_seq=1 ttl=238 time=129 ms

--- 72.14.207.99 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 129.714/129.714/129.714/0.000 ms

```

(You can also try: "host hostname.com" to test this, but I'm wondering if its your nameserver or your internet connectivity thats acting up here.)

If the first one fails, but second works it means it can't resolve the hsotname to an IP address. If this is the case there is something wrong in the file /etc/resolve.conf gl with fixing this issue.

Unless you can be more specific about your issue I can't help you any further as I never had an issue quite like it so never wondered about fixing it.

---

### Post by JNowka on 2006-01-20
Thank you for your help but i figured out the problem.

I had uncheck the box that said "Assign the default route to this gateway"

Thank you for your time, it is much appreciated

PS
I am responding from my linux box now :D

---

