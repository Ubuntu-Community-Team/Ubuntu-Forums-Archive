---
title: "Two Ports instead of one"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-04-16
ok I have ssh setup where I Can remotely login. But Is it possible to have more than one port?
```
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
```
i want port 22 and port 5190

---

### Post by profXavier on 2007-04-16
Well, if you read, in the comments, it says ports, with an 's'. SO I would suspect you could use a comma (and no space) between two or more ports.

---

### Post by ProjectWhat on 2007-04-16
It would be
```

Port 22
Port 5190
Port ...

```
Then u would need to resart it. which i couldt get to work so i resarted my PC

---

### Post by Fascination on 2007-04-16
The way you've done it should work and then run "sudo /etc/init.d/ssh restart" (or reboot). Does it refuse to connect to your new port number? If you have a router or similar, have you remembered to set up the new rule for the new port? A colleague of mine changed his port number to something obscure but left his DMZ set to 22 which of course threw a spanner in the works. :)

---

