---
title: "terminal"
date: 2012-02-29
forum: Any Other OS
---

### Post by Karlof on 2012-02-29
Hi forum

I am using fuduntu the terminal will not 
accept sudo  commands 

Help please

---

### Post by nothingspecial on 2012-02-29
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by winh8r on 2012-02-29
Which commands are you trying to run? And what error message are you receiving?

---

### Post by Karlof on 2012-02-29
Hi the command sudo apt-get update


reply sudo;apt-get command not found

P S to assume I  know what I am doing with linux and its different

not joined up distros as a newbie is naive to say the least

---

### Post by matt_symes on 2012-02-29
Hi

From here.

[http://en.wikipedia.org/wiki/Fuduntu](http://en.wikipedia.org/wiki/Fuduntu)

> Fuduntu Linux is a **Fedora-based Linux distribution** created by Andrew Wyatt. 

If so then is suspect it uses yum and not apt. Therefore apt-get will not work as it uses a different package manager.

Kind regards

---

### Post by winh8r on 2012-02-29
Think this page might help you as you might be using yum:

[http://www.fedorafaq.org/#installsoftware]("http://www.fedorafaq.org/#installsoftware")

hope this helps

---

### Post by fuduntu on 2012-02-29
> **Karlof said:**
> Hi forum

I am using fuduntu the terminal will not 
accept sudo  commands 

Help please

I would normally direct you to Fuduntu Forum, but it is down while being migrated to a new provider.

Instead of sudo, we use beesu.

---

### Post by fuduntu on 2012-02-29
> **Karlof said:**
> Hi the command sudo apt-get update


reply sudo;apt-get command not found

P S to assume I  know what I am doing with linux and its different

not joined up distros as a newbie is naive to say the least

We are an rpm based distribution, that uses yum for package management.

---

### Post by Karlof on 2012-02-29
Hi thanks for your help

I have used yum now 

but it says I have to be root to use some of the commands

how do I become root

---

### Post by Karlof on 2012-02-29
Hi guys the beesu from the fuduntu contribution seems
to have solved the problem

cheers all and thanks 

ps can you let me know when the new fuduntu

site is ready I would like to join

Cheers karlof

 ps we newbies would get nowhere without you

guys thanks again all of you

---

### Post by snowpine on 2012-02-29
Whoops, I've been using Fuduntu for a couple of months and this is the first time I've even heard of 'beesu' (should have read the documentation, heh). Have I messed up my system in any way by using 'su -' like other RPM distros?

---

### Post by raja.genupula on 2012-02-29
> **Karlof said:**
> Hi guys the beesu from the fuduntu contribution seems
to have solved the problem

cheers all and thanks 

ps can you let me know when the new fuduntu

site is ready I would like to join

Cheers karlof

 ps we newbies would get nowhere without you

guys thanks again all of you

[http://www.fewt.com/2012/02/fundraiser-improving-hosting-and.html](http://www.fewt.com/2012/02/fundraiser-improving-hosting-and.html)

---

### Post by fuduntu on 2012-02-29
> **snowpine said:**
> Whoops, I've been using Fuduntu for a couple of months and this is the first time I've even heard of 'beesu' (should have read the documentation, heh). Have I messed up my system in any way by using 'su -' like other RPM distros?

beesu is just a graphical wrapper for su.  In the end, it doesn't matter how you get there though.  :)

---

