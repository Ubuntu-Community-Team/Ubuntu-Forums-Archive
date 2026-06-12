---
title: "Simple ssh setup"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by Hospadar on 2007-11-08
I'm wanting to setup my computer as an SSH host, so that I can connect to it from elsewhere to get at files and do work away from home and whatnot.

I might actually have it setup correctly, but am not connecting properly.  I've been doing ```
ssh <my username>@<my IP address>
```

I've installed ssh, and from my machine, I can do an "ssh localhost" and that works fine, but when I try to connect from other machines, it just hangs and does not connect at all (with no error messages).  Do I need to do some reconfiguring with IPtables to open up port 22?  If so, how do I do that?

---

### Post by jordanmthomas on 2007-11-08
Add this to /etc/hosts.allow
```

sshd:  ALL

```

That should fix you right up.

**edit** do this on the server box.

---

### Post by hyper_ch on 2007-11-08
on the machine you want to ssh into you need to setup the ssh server:

```

sudo apt-get install openssh-server

```

---

### Post by jordanmthomas on 2007-11-08
I thought he had already done this since he can ssh in if he's physically at the computer?

---

### Post by hyper_ch on 2007-11-08
Oh, didn't see that...

installting the ssh daemon should not require to change anything on iptables.

---

### Post by jordanmthomas on 2007-11-08
In Arch I had to add that to my hosts.allow, is that needed in Ubuntu (not sure)?

Another thing for the OP to check is if he's behind a router, that port 22 is forwarded to his server.

---

### Post by hyper_ch on 2007-11-08
It's not needed for Ubuntu. iptables in Ubuntu - as far as I know - is permissive - meaning no ports are closed but upon a normal installation no services are listening...

---

### Post by Hospadar on 2007-11-09
Hey, thanks for the answers, I'm not behind a router, I'll give that a try today.

---

### Post by Dr Small on 2007-11-09
> **Hospadar said:**
> Hey, thanks for the answers, I'm not behind a router, I'll give that a try today.
[http://php.8ez.com/drsmall/blog/?p=124](http://php.8ez.com/drsmall/blog/?p=124)

---

