---
title: "MySQL - Using in Ubuntu - Security"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-02-20
Hi, forgive my ignorance in this matter:

I'm running Ubuntu 7.10 and I want to use start using a local MySQL database. I need to install MySQL first, but before I do Id like to ask a few questions:

First, is it just as simple as installing mysql from synaptic or do I need to do some elaborate configuration before of afterwards?

Next, should I install mysql and use a database or two, is are there any security implications for my machine? For example, is using mysql going to create a server of some kind that can be accessed from outside my machine, or would specific ports needs to be closed via IPTables to prevent this.

Sorry if this is a silly question, but I'm fairly new into Ubuntu from Windows, and my only experience with mysql is knowing that its the backend database for lots of online forums.

---

### Post by freebeer on 2008-02-20
Are you behind a router?  If so, the router will act as a firewall (through NAT).  So unless you specifically forward ports in your router, you should be fine.

Normally the default Ubuntu installation has everything closed.  It's only when you open a specific service could you be exposed.  I'm no expert (I'm still learning about all of this), but  unless you've got a specific security concern, you should be fine.

If you really want to nail it down, post up on the Security Discussion forum.

FWIW, I run MySQL and Apache and have had no security issues.

---

### Post by az on 2008-02-20
> **MaxVK said:**
> Hi, forgive my ignorance in this matter:

I'm running Ubuntu 7.10 and I want to use start using a local MySQL database. I need to install MySQL first, but before I do Id like to ask a few questions:

First, is it just as simple as installing mysql from synaptic or do I need to do some elaborate configuration before of afterwards?

Next, should I install mysql and use a database or two, is are there any security implications for my machine? For example, is using mysql going to create a server of some kind that can be accessed from outside my machine, or would specific ports needs to be closed via IPTables to prevent this.

Sorry if this is a silly question, but I'm fairly new into Ubuntu from Windows, and my only experience with mysql is knowing that its the backend database for lots of online forums.
See here:
[https://help.ubuntu.com/community/ApacheMySQLPHP#head-39085275bc28194cca77d021ec362ff3003b10bc](https://help.ubuntu.com/community/ApacheMySQLPHP#head-39085275bc28194cca77d021ec362ff3003b10bc)

By default, mysql-server does not listen to the network, so you will be fine.  

You will need to set the mysql-root password.

---

### Post by MaxVK on 2008-02-21
Thanks guys.

Yes I'm behind a router, and I already have IPTables set up to block everything except those ports that I specifically allow. Windows paranoia is just hard to shake off I think!

Iv skimmed those links and Ill go back and check them fully before I actually do anything.

Thanks again

Max

---

### Post by njparton on 2008-02-21
When installing mysql it asks you a load of questions like password etc which should get you up and running with a simple set up.  As always there are then config files to edit if you want something more elaborate.

---

### Post by hyper_ch on 2008-02-21
Chapter 13 - MySQL installation

[http://www.howtoforge.com/perfect_server_ubuntu7.10_p4](http://www.howtoforge.com/perfect_server_ubuntu7.10_p4)

---

