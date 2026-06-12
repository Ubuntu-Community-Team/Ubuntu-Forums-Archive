---
title: "Server at startup that requires input"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by livet0ski on 2005-12-16
Hey everyone,
I have a quick question. I have a server the I want to start at startup. I'm guessing that I would put a symlink in /etc/init.d/ and then have it run at startup, the only problem is that this server requires a password right after startup. There no options to put the password in at startup of the server, but about 2 seconds after startup, it asks for a password. I obviously know the password, but I'm trying to make it so i can just turn on my Ubuntu box and leave it. How would I do this?
Thanks,
Pat

---

### Post by livet0ski on 2005-12-17
anyone??

---

### Post by bscbrit on 2005-12-17
I'm trying to think which server needs a password _to start_.  Many of them need one to change various settings but my http and mail servers are configured by  files and do not need a password to start.  Can you confirm that your server needs a password at start up?

---

### Post by livet0ski on 2005-12-17
yea im sure, if u really wanna know its a WASTE server for private encrypted p2p networking, i'm not too fimiliar with the whole linux scripting deal
thanks,

pat

---

### Post by bscbrit on 2005-12-17
I take it this is not from an Ubuntu package - or, at least, I couldn't find it in my repos?  I'm sorry, but I cannot help on this one.  Best of luck!

---

