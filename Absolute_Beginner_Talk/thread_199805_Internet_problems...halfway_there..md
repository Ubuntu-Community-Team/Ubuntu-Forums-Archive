---
title: "Internet problems...halfway there."
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by cookfromfrozen on 2006-06-19
Hey guys,
I'm typing this message from Ubuntu, so I must be halfway there with the net connectivity problems. :D 

Firefox was slow so I disabled IPV6 in about:config and also did the bad_list trick.  Firefox is working fine but nothing else works e.g. Gaim just says "Connecting..." forever.

ping google.com works and the "Network Tools" applet seems to be resolving names, but when I try something like "host google.com" I get this:

```
google.com has address 72.14.207.99
google.com has address 64.233.187.99
google.com has address 64.233.167.99
;; Warning: Message parser reports malformed message packet.
;; connection timed out; **no servers could be reached**

```

Not sure what to make of this.  It resolves all the IPs for google.com, but then says no DNS servers could be reached. :confused:   I think this is what is causing the other apps to stumble.  Firefox must be smart enough because it works.

I've heard I should set ubuntu to use my ISPs DNS server addy instead of my router gateway (192.168.1.1), but how do I find that out?

BTW. ip a | grep inet6 doesn't show any output so at least I know IPV6 is actually gone.

---

### Post by steve.horsley on 2006-06-19
It looks like your DNS sever may have a problem, but this may be irrelevavnt - your basic name lookup seems functional.

Here is my output:> steve@dingly:~$ host google.com
google.com has address 64.233.167.99
google.com has address 64.233.187.99
google.com has address 72.14.207.99
google.com mail is handled by 10 smtp3.google.com.
google.com mail is handled by 10 smtp4.google.com.
google.com mail is handled by 10 smtp1.google.com.
google.com mail is handled by 10 smtp2.google.com.
steve@dingly:~$
steve@dingly:~$
steve@dingly:~$ dig google.com

; <<>> DiG 9.3.2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 54226
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             254     IN      A       64.233.167.99
google.com.             254     IN      A       64.233.187.99
google.com.             254     IN      A       72.14.207.99

;; AUTHORITY SECTION:
google.com.             299491  IN      NS      ns1.google.com.
google.com.             299491  IN      NS      ns2.google.com.
google.com.             299491  IN      NS      ns3.google.com.
google.com.             299491  IN      NS      ns4.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.         300051  IN      A       216.239.32.10
ns2.google.com.         300051  IN      A       216.239.34.10
ns3.google.com.         300051  IN      A       216.239.36.10
ns4.google.com.         300051  IN      A       216.239.38.10

;; Query time: 19 msec
;; SERVER: 194.106.56.6#53(194.106.56.6)
;; WHEN: Mon Jun 19 22:58:37 2006
;; MSG SIZE  rcvd: 212



Try looking at the output of **netstat** while gaim is saying connecting... and see if there is a line that is in the **SYN SENT** state. If there is, this is an indication that a connect request has been sent but no confirmation received - that's possibly a network problem outside your control.

---

### Post by uzi09 on 2006-06-19
u can ping sites, obviously come onto ubuntuforums.org, but can't connect gaim?

i'd say it would be a firewall issue. are you using a router?? do you have the correct ports forwarded for gaim (and anything else that needs the net)??

---

