---
title: "Gmail Authentication Problem?"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by thalamus on 2005-11-21
I was trying to set-up my Gmail account with Evolution and all looked well except I can't receive anything. When it shows my connections, the SMTP connected fine but the POP didn't. I followed the instructions on Gmail's site the best I could and am still having problems? Is there an authentication issue? or could it be something else?

---

### Post by suRoot on 2005-11-21
Are you behind a firewall?  As best I remember, gmail uses non-standard ports for pop & smtp.  Some firewalls block all ports not allowed by the administrator.  Perhaps this is your problem.

What error do you get specificially?  Or do you even get one?  What happens if you do the following from a terminal?

```
telnet pop.gmail.com 995
```

---

### Post by thalamus on 2005-11-23
I'm not behind any firewalls that I know of. I don't get any error message other than the connection times out while waiting to connect. And I typed that line into a terminal and it said it connected. Still, clueless.

---

