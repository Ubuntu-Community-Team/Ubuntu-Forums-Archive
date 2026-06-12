---
title: "Problems connecting to an email account with Evoloution."
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by yompaz on 2007-12-22
Hi - I'm new to Ubuntu (using 7.10), and have been trying to setup evoloution. I have successfully connected to gmail, but when I try and connect to another of my mail accounts, o2.ie, I get the following error:
"failed to read a valid greeting from POP server pop3.o2.ie"
I've checked and rechecked my settings, and they look ok.
Has anyone seen this before?
:confused:

---

### Post by dcstar on 2007-12-22
> **yompaz said:**
> Hi - I'm new to Ubuntu (using 7.10), and have been trying to setup evoloution. I have successfully connected to gmail, but when I try and connect to another of my mail accounts, o2.ie, I get the following error:
"failed to read a valid greeting from POP server pop3.o2.ie"
I've checked and rechecked my settings, and they look ok.
Has anyone seen this before?
:confused:

Open a terminal and enter:

```
telnet pop3.o2.ie 110
```

If you get this then you network connection is ok:
```
Trying 62.40.32.37...
Connected to mail.o2.ie.
Escape character is '^]'.
+OK O2 Ireland POP3 service (1) ready.
```

If not, then you have a connectivity/firewall problem.

---

