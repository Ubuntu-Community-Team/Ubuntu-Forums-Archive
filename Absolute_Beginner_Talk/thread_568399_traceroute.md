---
title: "traceroute"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by aozkaya on 2007-10-05
Hi I try to install traceroute it asked me to install the dependencies which is libc6. so I install it but right  now it says that there is a conflict with libc6 and tzdata. 
Is there any way that I can download traceroute to my system?

Thank you,
aozkaya

---

### Post by aspen_dv on 2007-10-05
did you try
sudo apt-get install traceroute

---

### Post by aozkaya on 2007-10-05
no because I have no internet connection. I am working in a close network. there is many pc that communicates each other without internet connetion

---

### Post by wormser on 2007-10-05
Maybe you could try  tcptraceroute instead.  It might not have the same dependences and is worth a shot.  I am not sure how to resolve the conflict but that may be a work around.

---

### Post by aozkaya on 2007-10-09
Ok Thank you,
Do you know the differences between tcptraceroute and traceroute?

Thanks,
aozkaya

---

### Post by wormser on 2007-10-13
> **aozkaya said:**
> Ok Thank you,
Do you know the differences between tcptraceroute and traceroute?

Thanks,
aozkaya

I got the following quote from [here]("http://michael.toren.net/code/tcptraceroute/").

>  tcptraceroute is a traceroute implementation using TCP packets.

The more traditional traceroute(8) sends out either UDP or ICMP ECHO packets with a TTL of one, and increments the TTL until the destination has been reached. By printing the gateways that generate ICMP time exceeded messages along the way, it is able to determine the path packets are taking to reach the destination.

The problem is that with the widespread use of firewalls on the modern Internet, many of the packets that traceroute(8) sends out end up being filtered, making it impossible to completely trace the path to the destination. However, in many cases, these firewalls will permit inbound TCP packets to specific ports that hosts sitting behind the firewall are listening for connections on. By sending out TCP SYN packets instead of UDP or ICMP ECHO packets, tcptraceroute is able to bypass the most common firewall filters. 

---

