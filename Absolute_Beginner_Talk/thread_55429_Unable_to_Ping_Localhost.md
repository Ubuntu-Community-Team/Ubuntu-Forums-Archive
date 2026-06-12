---
title: "Unable to Ping Localhost"
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by suma on 2005-08-08
Hey there...

I have just finished setting up a firestarter policy on my ubuntu box. I was testing out various things, when i discovered that I'm unable to ping localhost... I tried enabling ICMP echo request and reply options, and shutting down firestarter altogether - however im still not able to ping. Ping to external host works fine... could there be a problem with my loopback address?


How should I go about resolving this issue?
Thanks in advance,
Suma

---

### Post by tom-ubuntu on 2005-08-09
Don't know firerstarter that good, but did you activate your new rule? Is localhost in your /etc/hosts?

---

### Post by suma on 2005-08-09
Hey joeuser thanks for replying...

Yes i did apply the new config, however I'm fairly certain that the problem is not caused by firestarter, because even when i shut down firestarter completely, i still cannot ping. 

I'm very new to linux, so im not quite sure what /etc/hosts is for, however it appears to include localhost... here is the compete file:

user@P1C7UR3-1:/$ cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost       P1C7UR3-1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Here is some output from ifconfig:

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1340466 (1.2 MiB)  TX bytes:1340466 (1.2 MiB)


It appears that the loopback interface is not assigned an address, however this is based on nothing more than a guess.

Cheers,
suma



EDIT: Here is the output from ping localhost... it *does* resolve it to 127.0.0.1

user@P1C7UR3-1:/$ ping localhost
PING localhost.localdomain (127.0.0.1) 56(84) bytes of data.

--- localhost.localdomain ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms

---

### Post by varunus on 2005-08-09
This happens even when firestarter is off (choose stop firewall inside firestarter)?  Can you post the output of ifconfig in a terminal?

Did you bychance skip the "configuring network interfaces" step during bootup?

---

### Post by suma on 2005-08-10
After extensive testing, I have come to the conclusion that firestarter is messing things up. I have decided to set up a router, and forget about firestarter altogether.
(Loopback problem was not the only thing that made me decide to do this).


Thanks for help anyways.

Cheers,
Suma

---

