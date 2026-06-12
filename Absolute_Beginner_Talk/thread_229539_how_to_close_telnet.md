---
title: "how to close telnet ???"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-08-04
after I've installed the debian menu
I say I have telnet
it's very unsecure
even in winxp sp2 it's closed by default
why isn't it closed in ubuntu ???
how do I close it ???

---

### Post by Tomosaur on 2006-08-04
Are you sure it's running, or you just have it installed?

---

### Post by patrick295767 on 2006-08-04
> **MAXDDARK said:**
> after I've installed the debian menu
I say I have telnet
it's very unsecure
even in winxp sp2 it's closed by default
why isn't it closed in ubuntu ???
how do I close it ???

Telnet ?? 

Think ssh !! That'll be secured !
ssh hostmachine

---

### Post by MaximB on 2006-08-04
I can open it
that means that it isn't closed
and anybody can hack into my computer
it's in debian>apps>net>telnet
how do I close it ?
and why it isn't closed by default ?

---

### Post by Tomosaur on 2006-08-04
For someone to run telnet, they must already have hacked into your computer. Don't worry about it.

---

### Post by MaximB on 2006-08-04
no man
in windows if you know somones IP you can use telnet to hack into his computer without him ever know about it
that's why they closed the telnet port in winxp sp2

---

### Post by 5-HT on 2006-08-04
If you haven't manually installed a telnet server, or if one was not installed as a recommended package/dependencie, it may be just the telnet client that is installed by default. If it's just the client, there are no worries as no one can connect to your box: it's only a client for outgoing connections to another machine.

To find out, could you do the following to see which telnet package may be installed (it'll have an 'i' on the left of the output):
```
 aptitude search telnet 
```

---

### Post by RhettBastid on 2006-08-04
If you are running your computer through a firewall, all you have to do is close port 25 on the firewall.  Then, no one outside your LAN will be able to telnet with anything behind the firewall.  if you're using a router, it will have a firewall built into it.  

As far as on your computer itself, I know there are ways to do it by changing a file, but I don't remember how.  Maybe someone else can help.

---

### Post by Tomosaur on 2006-08-04
> **MAXDDARK said:**
> no man
in windows if you know somones IP you can use telnet to hack into his computer without him ever know about it
that's why they closed the telnet port in winxp sp2

Linux isn't windows, welcome to security :P

---

### Post by jimmygoon on 2006-08-04
Did you click Debian -> Apps -> Net -> Telnet... ITS A CLIENT!

1) The telnet server isn't running, in fact I'm sure that there isn't a telnet server installed by default, for the exact same reason that ssh isn't installed by default

2) Telnet on xp is only insecure because of bad user practices (running all users as admin w/o passwords!!!)

3) Use SSH if you have to use anything anyways... its secure ;)

---

### Post by MaximB on 2006-08-04
I have only the client...wow....and I thought....
thanks

---

### Post by MaximB on 2006-08-04
Jimmygoon - why do you have the coffe cup and I don't ? :):):)

---

