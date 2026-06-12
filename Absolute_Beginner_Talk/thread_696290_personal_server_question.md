---
title: "personal server question"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-02-13
Hi

I'm pretty sure that I've set up everything I need to on my server.

- I've got LAMP set up fine
- I've installed webmin
- I followed a DNS tutorial to setup bind ([here)]("http://ubuntuforums.org/showthread.php?t=236093")
- I set up port forwarding on my router to send port 80 requests to 192.168.1.100 (which is my server and is a static IP)

Now what do I do about making my domain point there?  Bind is set to ns1.blah.net - so do I just change my dns settings at my registrar?  I don't see how that works!

Can anyone point me in the right direction please?

Thanks very much

---

### Post by nemilar on 2008-02-13
If you're going to be running the nameserver inside your network, then configure your registrar to use your network's address as the nameserver, and be sure to forward the appropriate port in your router.

If you're not using your own nameserver, just configure whichever nameserver you are using (for example, one provided by the registrar) to have the domain point to your network address.

---

### Post by Squizz on 2008-02-13
> **nemilar said:**
> If you're going to be running the nameserver inside your network, then configure your registrar to use your network's address as the nameserver, and be sure to forward the appropriate port in your router.

If you're not using your own nameserver, just configure whichever nameserver you are using (for example, one provided by the registrar) to have the domain point to your network address.

I'd prefer to run my own nameserver, although to be honest I've been following tutorials blindly regarding bind so I'm not sure if I've set it up properly or not.  In my bind configurations I've set up ns1.simontucker.net, and if I use the dig command from the server I get

```

; <<>> DiG 9.4.1-P1 <<>> simontucker.net
;; global options; printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 50188
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;; simontucker.net.                     IN                 A

;; Query time: 102 msec
;; SERVER: 192.168.1.100 53(192.168.1.100)
WHEN: Thu Feb 14 03:18:09 2008
;; MSG SIZE  rcvd: 33

```

Whereas if I do that from another machin, then I get

```

; <<>> DiG 9.4.1-P1 <<>> simontucker.net
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12789
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;simontucker.net.               IN      A

;; ANSWER SECTION:
simontucker.net.        5825    IN      A       67.15.45.36

;; AUTHORITY SECTION:
simontucker.net.        77825   IN      NS      ns2.msshost.com.
simontucker.net.        77825   IN      NS      ns1.msshost.com.

;; Query time: 49 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Thu Feb 14 03:22:41 2008
;; MSG SIZE  rcvd: 96

```

The second is where the domain is currently hosted.

Have I set it up right - if so, how do I go about configuring it to use my network address?

---

### Post by Squizz on 2008-02-14
If it helps, I can access my server externally through my WAN IP address - [http://213.40.113.197/](http://213.40.113.197/) - but I want to link that to a name server that I make myself, but I'm not sure how to go about doing it.

---

### Post by Squizz on 2008-02-14
Last bump.  For now, I'm using awake.org to reroute to my IP in case anyone else is stuck and this doesn't get resolved.

---

