---
title: "ssh"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by uncreative on 2007-02-10
My web host told me to ssh into my account on port 2222

so i open up terminal and type:

ssh [email]username@ip.add.dre.sss[/email]:2222 

and that doesnt seem to work, what am i missing?  befoer when it was on the standard port it always worked like that

---

### Post by jordanmthomas on 2007-02-10
Have you configured it specifically to listen on port 2222?
By default it is port 22 (as it seems you know)

The configuration file you need to look at is 
```
/etc/ssh/sshd_config
```

**actually, it looks like you may be trying to connect to their servers, so you probably don't have access to this.  Sorry.

---

### Post by karamba_kid on 2007-02-10
Change the port to 2222 in the file mentioned above (/etc/ssh/sshd_config) then restart the ssh server (sudo /etc/init.d/ssh restart) and then to ssh to that machine you do (ssh -p 2222 user@hostname).

---

### Post by kanna1620 on 2007-02-12
> **karamba_kid said:**
> Change the port to 2222 in the file mentioned above (/etc/ssh/sshd_config) then restart the ssh server (sudo /etc/init.d/ssh restart) and then to ssh to that machine you do (ssh -p 2222 user@hostname).
I did what you said but it gives me error saying that 
**ssh: restart: Name or service not known**
What should I do?

---

### Post by jordanmthomas on 2007-02-12
It's sshd

---

