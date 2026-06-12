---
title: "how do I tell who is logged on to my sshd?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-01
Bueller?

---

### Post by joesmith1234 on 2008-02-01
and does sshd log connection information at all?

---

### Post by PeterJS on 2008-02-01
If you're looking for information right this second, *who* will tell you who is logged in. Don't know about default logging set up.

---

### Post by joesmith1234 on 2008-02-01
> **PeterJS said:**
> If you're looking for information right this second, *who* will tell you who is logged in. Don't know about default logging set up.

is there a way to boot users?  like, if I accidentally stayed logged in at work, and I wanted to free up my irc nick...

---

### Post by bodhi.zazen on 2008-02-01
> **joesmith1234 said:**
> is there a way to boot users?  like, if I accidentally stayed logged in at work, and I wanted to free up my irc nick...

EDIT: You need to do a little more then my original post :(

1. List connected users with :

```
who
```

2. Determine the PID (process id) with ;

```
who -all | grep <user>
```

3. Kill the session:

```
sudo kill -i <PID>
```where <PID> is the process ID.

> bodhi@VirtualUbuntu:~$ who
bodhi    tty11        2008-01-30 21:47 (:0)
bodhi    pts/2        2008-02-01 16:25 (IP address)
bodhi    pts/3        2008-01-30 21:48 (:0.0)

bodhi@VirtualUbuntu:~$ who -all | grep bodhi
bodhi    + tty11        2008-01-30 21:47  old         1583 (:0)
bodhi    + pts/2        2008-02-01 16:25   .         **26620** (IP address)
bodhi    + pts/3        2008-01-30 21:48  old         1783 (:0.0)

bodhi@VirtualUbuntu:~$ sudo kill -1 **26620**  #< -- Note: that is the number 1 and not a small "L"

4. Now this will, of course, not prevent the user from logging back in, for that you need to secure your ssh server. See [uwiki]AdvancedOpenSSH[/uwiki]

---

### Post by docshawnc on 2008-02-01
Can you see the process ID?  

ps -A |more

if so, just kill it

---

### Post by PeterJS on 2008-02-01
Once again poor reading comprehension gets me. I crafted up a script to make booting users simpler, only to realize that if the user you were trying to boot was the same user you were logged in as it would be problematic. It's available on request, but really doesn't solve the problem as elegantly as I'd hoped.

---

