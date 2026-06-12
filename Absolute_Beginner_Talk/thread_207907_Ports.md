---
title: "Ports?????"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-07-02
I usually connect to my file server from Port 22 but for some reason I tried to connect to it today remotely using PuTTY and SSH and I didn't let me.  Is there a way to find out if port 22 is closed or a way to configure it?  Please help any advice is useful.:confused:

---

### Post by digimars on 2006-07-02
```

netstat --numeric-ports

```

See if that shows anything for you.

```

man netstat

```
Will bring up some useful information.

Are you running a firewall (such as Firestarter)?

---

### Post by NeoGreen on 2006-07-02
I don't think I am.  I'll try the command. Thanks.

---

### Post by NeoGreen on 2006-07-02
I tried the command but I don't see port 22.  Where can I go to enable Port 22?:confused:

---

### Post by steve.horsley on 2006-07-02
try this:
**sudo /etc/init.d/ssh start**

---

### Post by NeoGreen on 2006-07-02
I tried it and I get a fail message.:confused:   should I stop then restart?

---

### Post by b1g4L on 2006-07-02
You could run a port scan on your IP. Correct me if I'm wrong, but that should tell you ports which are listening.

---

### Post by NeoGreen on 2006-07-02
I stopped it and restarted it.  Nothing:confused:

---

### Post by NeoGreen on 2006-07-02
How do I run a ports scan?  What is the command?:confused:

---

### Post by verbatim210 on 2006-07-02
i have the same problem but im trying to open 23 instead.

if u do **netstat -plantu **it will tell you what ports are opened.

---

### Post by b1g4L on 2006-07-03
System --> Admin --> Network tools --> port scan tab

---

### Post by steve.horsley on 2006-07-03
[QUOTE=NeoGreen]I tried it and I get a fail message.:confused:   should I stop then restart?[/QUOTE]
Please, when you get an error message, post it so we can see what's going wrong. 

You could try restart, but my guess is that the daemon isn't running anyway. What is the error message when you try to start it?

---

### Post by NeoGreen on 2006-07-03
Sorry, I should have been more specific.  It just gets to me because it was working fine and all of a sudden it stoppped working.  I will post the message in a while.  I am at:D  work.

---

### Post by atoponce on 2006-07-03
[quote=NeoGreen]Sorry, I should have been more specific.  It just gets to me because it was working fine and all of a sudden it stoppped working.  I will post the message in a while.  I am at:D  work.[/quote]

Are you protected by a firewall, hardware or software?  If so, do you have the port open there?  For example, if protected by a router, is port 22 open in the router?  Silly quiestion, I know, but very commonly overlooked.

---

### Post by NeoGreen on 2006-07-05
Didn't even bother to check that, I'll check it out thanks :)

---

