---
title: "Problem with ntpdate.."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by dupa on 2007-06-11
Why i get this error?

```

$ sudo ntpdate -v ntp.ubuntu.com
11 Jun 11:14:15 ntpdate[19775]: ntpdate 4.2.2p4@1.1585-o Wed Mar  7 20:43:31 UTC 2007 (1)
11 Jun 11:14:19 ntpdate[19775]: no server suitable for synchronization found

```

---

### Post by ajmorris on 2007-06-11
> **dupa said:**
> Why i get this error?

```

$ sudo ntpdate -v ntp.ubuntu.com
11 Jun 11:14:15 ntpdate[19775]: ntpdate 4.2.2p4@1.1585-o Wed Mar  7 20:43:31 UTC 2007 (1)
11 Jun 11:14:19 ntpdate[19775]: no server suitable for synchronization found

```

it would seem that ntp.ubuntu.com is down.

---

### Post by Stephen Howard on 2007-06-11
The command just worked okay for me.  Maybe try using the -d option (which will print some debug info).

---

### Post by dupa on 2007-06-11
> **Stephen Howard said:**
> The command just worked okay for me.  Maybe try using the -d option (which will print some debug info).

```
$ sudo ntpdate -d ntp.ubuntu.com
11 Jun 15:24:38 ntpdate[28663]: ntpdate 4.2.2p4@1.1585-o Wed Mar  7 20:43:31 UTC 2007 (1)
transmit(82.211.81.145)
transmit(82.211.81.145)
transmit(82.211.81.145)
transmit(82.211.81.145)
transmit(82.211.81.145)
82.211.81.145: Server dropped: no data
server 82.211.81.145, port 123
stratum 0, precision 0, leap 00, trust 000
refid [82.211.81.145], delay 0.00000, dispersion 64.00000
transmitted 4, in filter 4
reference time:    00000000.00000000  Thu, Feb  7 2036  7:28:16.000
originate timestamp: 00000000.00000000  Thu, Feb  7 2036  7:28:16.000
transmit timestamp:  ca17cb99.d1f49060  Mon, Jun 11 2007 15:24:41.820
filter delay:  0.00000  0.00000  0.00000  0.00000
         0.00000  0.00000  0.00000  0.00000
filter offset: 0.000000 0.000000 0.000000 0.000000
         0.000000 0.000000 0.000000 0.000000
delay 0.00000, dispersion 64.00000
offset 0.000000

11 Jun 15:24:42 ntpdate[28663]: no server suitable for synchronization found
```

---

### Post by Stephen Howard on 2007-06-11
Hmm, I'm wondering if port 123 is blocked?  Try the -u option and see what happens.

---

### Post by dupa on 2007-06-12
> **Stephen Howard said:**
> Hmm, I'm wondering if port 123 is blocked?  Try the -u option and see what happens.

With -u, seems to have worked :)
Thanks

---

### Post by Stephen Howard on 2007-06-12
Good, it indicates that your router / firewall is blocking port 123.  Might be worth a snoop around and then open up the port.

---

### Post by cupa on 2007-06-12
"Good, it indicates that your router / firewall is blocking port 123."

According to my firewall administrator the port (123) is not being blocked.

Any ideas on what I can do now?

I'd really like to get ntpd-simple working, but I can't proceed if ntpdate won't even work on the standard port.



ntpdate -d doesn't work
ntpdate -u does work,

---

### Post by cupa on 2007-06-12
And the answer is...

The firewall is allowing the port to be open.
BUT the network address translation NAT rules are not forwarding my request over port 123.

So when your firewall administrator tells you the port is open, remember to have them check the NAT rules and ensure that your connection is actually getting to the firewall.


I figured it out by using TCPdump. An hour ago I hadn't a clue how to use TCPdump.
So I found this post and followed what greg did -- make two log files, one connecting successfully and one not.

[http://lists.ntp.isc.org/pipermail/questions/2005-September/006639.html](http://lists.ntp.isc.org/pipermail/questions/2005-September/006639.html)


The connection data that tcpdump captured was enough to show the firewall administrator that the problem was actually occurring. 


Hope this helps someone else trying to deal with an IT department that says there is no problem, it must be you.

---

### Post by private_meta on 2007-12-17
Hello!

I still have this problem on my machine, it says

ntpdate[4950]: no server suitable for synchronization found

the ports aren't the problem, even with a direct net connection i can't do the update
can someone tell me what else might be wrong here?

---

