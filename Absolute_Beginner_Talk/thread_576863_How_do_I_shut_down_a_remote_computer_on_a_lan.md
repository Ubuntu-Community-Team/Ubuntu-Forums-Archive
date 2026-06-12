---
title: "How do I shut down a remote computer on a lan"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by NULL712 on 2007-10-15
OK how do I shutdown a remote computer on a lan? both computers run ubuntu 7.04.
I want to do something like "shutdown -i" in winblows. Oh and can I use ubuntu to shut down a remote winbox on a lan?

Thanx
NULL712

---

### Post by KCPokes on 2007-10-15
Simplest way is to remote into the box (ssh) and issue the the shutdown command via a poweruser (or root).  Simply issue "sudo shutdown -h now" to shut it down immediately.  Your connection will be dropped once the other machine kills the SSH daemon.

---

### Post by nickj6282 on 2007-10-15
```
sudo halt
``` also works.

---

### Post by deserthowler on 2007-10-16
> **NULL712 said:**
> OK how do I shutdown a remote computer on a lan? both computers run ubuntu 7.04.
I want to do something like "shutdown -i" in winblows. Oh and can I use ubuntu to shut down a remote winbox on a lan?

Thanx
NULL712

I set up my Windows computers with tightVNC from their website and shutdown Windows machines by VNCing into them and following the normal shutdown procedure.  I use VNC with a Ubuntu machine and can shut it down remotely that way or, if I'm not logged in with VNC, I use ssh.

Earl

---

### Post by dwhitney67 on 2007-10-16
> **KCPokes said:**
> Simplest way is to remote into the box (ssh) and issue the the shutdown command via a poweruser (or root).  Simply issue "sudo shutdown -h now" to shut it down immediately.  Your connection will be dropped once the other machine kills the SSH daemon.

That will definitely work, however it seems unusual that someone would want to shutdown/halt a system that is managed remotely; there would be no way to turn it back on unless the operator (or someone else) is physically present to boot the system back up.

Anyhow, perhaps a reboot is all that is desired.  In that case, "sudo shutdown -r now" would be more appropriate.

---

### Post by good-morning on 2008-05-21
Hi,

Can I shutdown my Ubuntu at home from WinXP in my office?
I stupidly forgot to shutdown my PC when I left home this morning.

---

### Post by dwhitney67 on 2008-05-21
If you can ssh into your home PC, then yes you can.  (But why??)

You will need the IP address (or URL) of your system at home to ssh into it.

```
$ ssh userID@IPaddr
```

You will be prompted for a password.  Once you log in, you can shut the system down using:

```
$ sudo shutdown -h now
```

P.S. You will need an SSH-client (or similar application) at work in order to be able to ssh to your home computer.  If your computer is behind a firewall (e.g. a router) in which port 22 traffic is not being forwarded to the Ubuntu PC, then you will not be able to connect.

---

### Post by wdaniels on 2008-05-21
> **dwhitney67 said:**
> P.S. You will need an SSH-client (or similar application) at work in order to be able to ssh to your home computer.

I used to use [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") to SSH from Windows and I seem to remember it worked well.

---

### Post by good-morning on 2008-05-22
> If you can ssh into your home PC, then yes you can. (But why??)

You will need the IP address (or URL) of your system at home to ssh into it.

I guess I cannot do anything right now. Thanks anyway!

This tips looks useful.
[http://sudan.ubuntuforums.com/showthread.php?t=736509](http://sudan.ubuntuforums.com/showthread.php?t=736509)
I'll try to do this when I get home later.

What do noobs usually do to their remote desktop other than shutting down their PC?
-browsing files?
-playing games?... maybe not.:confused:

---

### Post by dwhitney67 on 2008-05-22
> **good-morning said:**
> 
What do noobs usually do to their remote desktop other than shutting down their PC?
-browsing files?
-playing games?... maybe not.:confused:
I never shut down my system, unless I feel that firefox has taken up too much memory.

As for what I do with ssh... software (system) maintenance, software development, and yes, browsing files.  I do not play games on my computer... for that I have an Xbox.

---

