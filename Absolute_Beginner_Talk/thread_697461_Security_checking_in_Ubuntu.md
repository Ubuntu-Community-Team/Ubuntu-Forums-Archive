---
title: "Security checking in Ubuntu?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-02-15
is there a program to check your System health?

---

### Post by Joeb454 on 2008-02-15
It depends what you mean by system health?

If you give a bit more detail we can have a look around :)

Just out of curiosity why do you want such a program?

---

### Post by adi_das on 2008-02-15
want to check whether my system is vulnerable or not vulnerable to attacks.

---

### Post by gvartser on 2008-02-15
There are several:

One of them are "chkrootkit"

To find more use synaptic or apt-cache and search for security.
```
apt-cache search security
```

But one good place to start is to check your log files on the system.
Located under /var/log

Another tip is to do a port scan of your machine to see what ports that are open & shut down those that are unused.

/g

---

### Post by Joeb454 on 2008-02-15
Well by default, Ubuntu has no ports opened except port 80 (somebody correct me if I'm wrong here)

And as for Viruses, there are very very few out in the wild for Linux (i.e. < 10) so you've not really got to worry about that because all the other viruses won't run on Linux unless you make them run in Wine :)

If you still want a program I'll have a look about :)

---

### Post by hyper_ch on 2008-02-15
> **Joeb454 said:**
> Well by default, Ubuntu has no ports opened except port 80 (somebody correct me if I'm wrong here)
Yes, you are wrong ;)

By default Ubuntu comes with all ports open BUT nothing (no service)  is listening on them. So they are open but no application will react if one of them is queried (sort of).

Once you install stuff, then there will be applications listening.

---

### Post by Joeb454 on 2008-02-15
I stand corrected :)

Though I'm actually sitting...so I *sit* corrected :p

---

### Post by skymera on 2008-02-15
sudo apt-get install tiger

use that, could be useful

---

### Post by kpkeerthi on 2008-02-15
Check out the stickies here

[http://ubuntuforums.org/forumdisplay.php?f=322](http://ubuntuforums.org/forumdisplay.php?f=322)

---

### Post by gvartser on 2008-02-15
> **Joeb454 said:**
> Well by default, Ubuntu has no ports opened except port 80 (somebody correct me if I'm wrong here)
And as for Viruses, there are very very few out in the wild for Linux (i.e. < 10) so you've not really got to worry about that because all the other viruses won't run on Linux unless you make them run in Wine


You are correct by default not many ports are open in the listening way, but while using and installing stuff on the machine ports will be open.

There are million's of hack attempts every day trying to get access of your machine to add them into so called bot nets.

For instance, if you have ssh server (22) open and a domain name attached to your network, check the syslog and you will see a lot of brute force attempts .. 

That is one of the reasons to why it is important to use non logical passwords, making it harder for them to attack.

Another example of why to check your open ports is that there are applications that are insecure by them self and that is a way in for a hacking attempt.

Take Oracle for an example, all Oracle databases uses a listener that allows clients to communicate with the server. Until version 10g of Oracle it was possible to remote administer a Oracle listener and this opened up for hackers to get access to the computer, by writing files onto the machine using the listener.

This way it is not hard to get access to an account, and then once you are in your in.. :(

So just because there are no viruses on linux does not mean that you should feel safe doing nothing. 

/g

---

### Post by Joeb454 on 2008-02-15
I didn't say you should feel safe...I just figured it'd be common sense to be careful when connected to the net - i.e. not connect to any public networks without a firewall running etc.

---

