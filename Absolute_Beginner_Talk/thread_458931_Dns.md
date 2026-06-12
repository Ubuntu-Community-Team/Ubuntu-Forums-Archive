---
title: "Dns ??"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by lupgop on 2007-05-30
when i installed ubuntu server - it installed some DNS software ...  any one know what this was called ? or have  a good guide to setting this up so i can access my system remotely ???

---

### Post by Bachstelze on 2007-05-30
BIND ? You don't need it if you're running only one server, just use a no-ip or dyndns redirection.

---

### Post by lupgop on 2007-05-30
sounds like what im looking for --- got any info on setting up   a no-ip or dyndns redirection ???

---

### Post by Bachstelze on 2007-05-30
[http://www.no-ip.org](http://www.no-ip.org)

---

### Post by lupgop on 2007-05-30
oh yes - my Ip is static....

---

### Post by dreadlord_chris on 2007-05-30
> **lupgop said:**
> oh yes - my Ip is static....

Well, that makes things a bit easier. Basically, DNS maps **human readable** names like [www.blah.com](www.blah.com) to an actual **IP address** that your computer understands - it's a convenience for us humans because most find it easir to remember a name than a string of numbers.

So, if you already know your IP and it's not gonna change - then DNS isn't *really* necessary.

Now, when you say you want to connect to you system remotely - how do you want to access it? Are you just looking for a remote shell or are you wanting a full remote desktop?

---

