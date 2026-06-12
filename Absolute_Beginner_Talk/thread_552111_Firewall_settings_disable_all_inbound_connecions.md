---
title: "Firewall settings: disable all inbound connecions"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by hooldus on 2007-09-16
1) How can I disable all inbound connections in Ubuntu 7 (something like "stealth mode").
Of course I still want to be able to surf the Internet.

2) By the way. I've heard, that there are some GUI for build-in firewall in Ubuntu. Is it necessary to install one?

Thank you in advance.

---

### Post by some_random_noob on 2007-09-16
1. You already are in a "stealth mode" - Ubuntu has only one port open after it's installed. Enable the universe repositories and install "nmap". Then do a portscan on your computer...

```
nmap -r 127.0.0.1
```

... that shows you how many ports are open. Chances are that nothing will be possible to exploit. If you're behind a router, then you are already very secure.

2. No, you don't need a graphical firewall. It is a cool thing to check out though - install "Firestarter" if you want. It's very small and quick to download. It just uses basic filtering rules and runs on top of "Iptables". (Iptables is a kernel-level filtering program, if I'm correct. It also requires a command line, unless you use something like Firestarter)

Edit: If you want everything blocked except internet, then use a "whitelist" in Firestarter - You're already pretty secure though. I have done nothing to secure my Ubuntu box, and I couldn't care less. :lol: It's fine.

---

### Post by hooldus on 2007-09-16
**some_random_noob**
Thanks for your response.
I tried nmap utility and got the following result:

```
Starting Nmap 4.20 ( http://insecure.org ) at 2007-09-16 14:55 EEST
Interesting ports on localhost (127.0.0.1):
Not shown: 1696 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.246 seconds
```

Is it normal, that 631 port is opened? Must I close it? (How?)

And one more question. Will ubuntu respond to ping and such stuff by default ?

---

### Post by hooldus on 2007-09-17
Is it a ***security leak*** ? (port 631)

---

### Post by lisati on 2007-09-17
> **hooldus said:**
> 1) How can I disable all inbound connections in Ubuntu 7 (something like "stealth mode").
Of course I still want to be able to surf the Internet.

2) By the way. I've heard, that there are some GUI for build-in firewall in Ubuntu. Is it necessary to install one?

Thank you in advance.
In addition to the comments already made, I make the following observation:
Many routers come with inbound protection (from the internet) turned on by default - at least the one I use from Netgear does.  Combine this with allowing only certain computers on through MAC access control, and wireless encryption, I'm fairly confident of intruders will be suffifiencly slowed down for me to notice in time if someone was up to mischief.

---

### Post by gary0 on 2007-09-17
> **hooldus said:**
> **some_random_noob**
Thanks for your response.
I tried nmap utility and got the following result:

```
Starting Nmap 4.20 ( http://insecure.org ) at 2007-09-16 14:55 EEST
Interesting ports on localhost (127.0.0.1):
Not shown: 1696 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.246 seconds
```

Is it normal, that 631 port is opened? Must I close it? (How?)

?

You have a shared printer on your network. It listens on port 631, don't close it or you won't be able to print across your network.
Gary.

---

### Post by some_random_noob on 2007-09-17
> **gary0 said:**
> You have a shared printer on your network. It listens on port 631, don't close it or you won't be able to print across your network.
Gary.

Yeah, that's true. I forget how you disable it, I found I guide via google once. Alternatively, I think it's called "CUPS" (Common Unix Printer Services???? :confused: ) So it's not too hard to kill. Certainly is a great feeling when it says there are 1000+ ports closed and none open :)

---

