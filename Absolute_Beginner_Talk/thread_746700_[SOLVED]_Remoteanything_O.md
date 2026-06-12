---
title: "[SOLVED] Remoteanything???? :O"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Nerdriot on 2008-04-05
Hi,

I recently ran nmap -P0 on my machine, to check for open ports. Here's what I got...

```
Not shown: 1693 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
4000/tcp  open  remoteanything
10000/tcp open  snet-sensor-mgmt

```

This sounds pretty unsafe. I'm a noob, but still. "Remoteanything" sounds relatively dangerous.

Anyone know what it is/what it does/if it's dangerous? If it how, how can I close it?

Thanks in advance!

---

### Post by skymera on 2008-04-05
Port 22 is open, follow this guide.

[http://forums.spry.com/showthread.php?t=98](http://forums.spry.com/showthread.php?t=98)

as for the rest, im not sure

---

### Post by Nerdriot on 2008-04-05
Wait, maybe I should rephrase what I said... I forgot to elaborate on one thing in particular, which could possibly change everything...

When I run nmap -P0 localhost, only one port is open, port 631.

When I run nmap -P0 <ip> (I'm on a network with one other computer, that runs Vista), it shows that the aforementioned ports are open (with remoteanything).

So does that mean that the other ports are NOT open on MY MACHINE, but maybe on another machine on this network?

I'm seriously a noob, so I'm sorry if I'm confusing.

---

### Post by skymera on 2008-04-05
run

```
 nmap -P0 localhost 
```

that will check ports on YOUR PC.

any ports then open arre on other PC's in the network, and you can laugh in their faces.

---

### Post by scxtt on 2008-04-05
the "remoteanything" could just be coming from /etc/services ... do **cat /etc/services | grep 4000** to see if it's defined ...

to see if anything is listening on 4000, do **sudo netstat -an | grep 4000** or **sudo lsof | grep 4000** and see what results you get ...

---

### Post by Nerdriot on 2008-04-05
> **skymera said:**
> run

```
 nmap -P0 localhost 
```

that will check ports on YOUR PC.

any ports then open arre on other PC's in the network, and you can laugh in their faces.

Oh, ok!

See, a while back, someone told me I could do this, with curl, to find out if any suspicious ports were open on my machine:

```
nmap -P0 $(curl www.whatismyip.org)
```

When I do that, I get that list I mentioned. I also get that list of ports I mentioned, if I do just the simple "nmap -P0 <ip>". When I do "nmap -P0 localhost", I get one port only.

So is curl finding open ports on the Windows machine on this network? That's pretty neat, hah...

Thank you!

---

### Post by Nerdriot on 2008-04-05
> **scxtt said:**
> the "remoteanything" could just be coming from /etc/services ... do **cat /etc/services | grep 4000** to see if it's defined ...

to see if anything is listening on 4000, do **sudo netstat -an | grep 4000** or **sudo lsof | grep 4000** and see what results you get ...

I checked /etc/services, and found nothing for "4000", so I went ahead and did the netstat | grep 4000, and the lsof | grep 4000, and it found nothing on either of those, either.

So I guess I'm clear? ;D

Thank you for the info, btw! I always make myself notes on how to check things, etc., and I've added this (which will equal me asking less noob questions in the future) :)

---

