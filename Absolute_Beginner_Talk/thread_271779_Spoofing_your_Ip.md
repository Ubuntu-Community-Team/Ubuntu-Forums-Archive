---
title: "Spoofing your Ip"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Malice007 on 2006-10-05
How do you spoof your ip using Ubuntu?

---

### Post by LookTJ on 2006-10-05
I don't think ubuntu supports IP spoofing

---

### Post by ubuntuuser on 2006-10-05
> **Taylor said:**
> I don't think ubuntu supports IP spoofing
Linux supports nearly everything you can imagine, also IP spoofing. I know that netcat is able to do IP spoofing, and I've heard of a tool named Mendax (but never used it). For your, let's say educational purposes, it would be much easier to write your own app. You can find more than enough C libraries all over the net that deal with this issue, or just write your own.

---

### Post by xyz on 2006-10-05
Sorry but what is spoofing?
Thanks.

---

### Post by D10 on 2006-10-05
It makes it look like an IP address other than yours, or a trusted address is sending/requesting information.

Here is a link to the defenition [http://www.webopedia.com/TERM/I/IP_spoofing.html](http://www.webopedia.com/TERM/I/IP_spoofing.html)

---

### Post by xyz on 2006-10-05
> **D10 said:**
> It makes it look like an IP address other than yours, or a trusted address is sending/requesting information.

Here is a link to the defenition [http://www.webopedia.com/TERM/I/IP_spoofing.html](http://www.webopedia.com/TERM/I/IP_spoofing.html)

Thanks a lot D10!

---

### Post by Anonii on 2006-10-05
> **xyz said:**
> Sorry but what is spoofing?
Thanks.
[http://www.securityfocus.com/infocus/1674](http://www.securityfocus.com/infocus/1674)

For MOAR and better info!

---

### Post by ubuntuuser on 2006-10-05
The problem with simple IP spoofing is that you won't receive any replies without further work, because all server replies would be sent to that faked IP. And it is rather simple for packet filters to recognize spoofed IPs coming in from outside the network. I don't know of a way to complete a full TCP three-way-handshake with spoofed IPs (doesn't necessarily mean anything :)), so it's hard to open a TCP connection using a fake IP, at least without stuff like a man-in-the-middle attack.

---

