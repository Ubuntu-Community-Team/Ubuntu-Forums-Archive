---
title: "Dynamic DNS for floating IP - can non-port 80s be supported?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Cheese Sandwich on 2007-05-16
Looks like port 80 is a no go for me, but port 423 works.

I've heard of dynamic DNS redirection, tying a domain name to floating IP, but can it also automatically tie to non-80 ports without the user having to include ":423" in the address?

---

### Post by lazyart on 2007-05-16
At dyndns.org it's called a webhop.  You'll create a second name that will redirect anywhere-- even to a different port.  You can even hide the redirection so the user doesn't know what's going on.

---

### Post by ironmonkeygf on 2007-05-16
I imagine that port 423 would work; I don't think Dynamic DNS is port specific.  I know I've used Dynamic DNS for ftp (port 21) and ssh (port 22).  You just have to enter it as DNS : port number (something like myDNS.com:423)

---

### Post by Bachstelze on 2007-05-16
No-IP has that feature too. The user just types [http://something.no-ip.org](http://something.no-ip.org) and it redirects to whichever port you wish.

---

### Post by Cheese Sandwich on 2007-05-16
Thanks I'll check those out.

---

