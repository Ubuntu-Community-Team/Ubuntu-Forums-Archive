---
title: "Wanted: Absolute Beginner's Guide to SSL"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by mrhinman on 2007-12-11
Okay, I want to set up SSL security on my Drake server.  Reason is that I'm hosting a database that needs the information to be encrypted.  The site will be on a static IP.

Will it need a domain name?  If so, how can set up DNS for it?

Also, if I acquire a certificate (thawte, CA-Cert, etc), how do I set it up?

Is there a beginner's guide to setting up SSL on Drake?

---

### Post by Dr Small on 2007-12-11
I don't know much about SSL, but I'm pretty sure you wouldn't need a domain, if you have a static IP address.

You would, for example, either connect to the site as:
[https://127.0.0.1](https://127.0.0.1)
or
[http://127.0.0.1:443](http://127.0.0.1:443)

As for aquiring a certificate, I have no idea, as I have never done it.

Dr Small

---

### Post by mrhinman on 2007-12-11
> **Dr Small said:**
> I don't know much about SSL, but I'm pretty sure you wouldn't need a domain, if you have a static IP address.

You would, for example, either connect to the site as:
[https://127.0.0.1](https://127.0.0.1)
or
[http://127.0.0.1:443](http://127.0.0.1:443)

As for aquiring a certificate, I have no idea, as I have never done it.

Dr Small

Well, I know how to acquire a cert.  I was just thinking you needed a domain to get one.  But, I have no idea how to set up SSL.  The web resources I've found are definitely not for noobs.

---

### Post by CaptainInsaneO on 2007-12-11
You don't need a domain name to use SSL, but you need to open port 443 on your web server to use the protocol.

You might have already seen this but here's a pretty nice howto on implementing SSL: [http://www.linux.com/base/ldp/howto/SSL-Certificates-HOWTO/index.html](http://www.linux.com/base/ldp/howto/SSL-Certificates-HOWTO/index.html)

---

### Post by mrhinman on 2007-12-12
Thank you!

---

