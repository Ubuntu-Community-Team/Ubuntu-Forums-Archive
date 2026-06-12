---
title: "check dns server working"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by dbrower256 on 2008-01-25
How do I check to see if the dns server in Ubuntu 7.10 Server is working?  If there is not a GUI for it, what commands do I need to type in terminal, which user do I need to be logged in as, and which directory do I have to be in?

Daniel

---

### Post by emarkd on 2008-01-25
Are you trying to check that the dns server your computer is using for resolution is working or are you trying to run your own dns server locally?  Are you having a problem that you could list?  That may be helpful.

---

### Post by arvevans on 2008-01-25
Go to a terminal screen (known as the Command Line Interface,  or CLI) and
type "man dig"
This will show you the user manual page for a DNS check tool that will let you do DNS probes on your own computer, a local DNS host, or any DNS host out there in the Internet.

Arv
_._

---

### Post by rhc on 2008-01-25
I didn't exactly understand your problem but
go to terminal
type
> sudo network-admin
Dns is there.

---

### Post by dcstar on 2008-01-25
> **dbrower256 said:**
> How do I check to see if the dns server in Ubuntu 7.10 Server is working?  If there is not a GUI for it, what commands do I need to type in terminal, which user do I need to be logged in as, and which directory do I have to be in?

Daniel

```
nslookup
```

---

### Post by dbrower256 on 2008-01-26
> **emarkd said:**
> Are you trying to check that the dns server your computer is using for resolution is working or are you trying to run your own dns server locally?  Are you having a problem that you could list?  That may be helpful.
I'm trying to see if the DNS service on my Ubuntu 7.10 Server is running.

---

### Post by dbrower256 on 2008-01-26
> **dcstar said:**
> ```
nslookup
```

Isn't there a command that will allow me to see if there is a process running the DNS service?

---

### Post by dcstar on 2008-01-26
> **dbrower256 said:**
> Isn't there a command that will allow me to see if there is a process running the DNS service?

```
ps
```

---

