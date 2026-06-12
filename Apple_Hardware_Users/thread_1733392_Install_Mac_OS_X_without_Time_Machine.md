---
title: "Install Mac OS X without Time Machine?"
date: 2011-04-19
forum: Apple Hardware Users
---

### Post by nl4m on 2011-04-19
I cannot install Mac OS X on my MacBook. When I boot from the DVD the  only option I get is to install the OS from Time Machine. I cannot do a  clean install from the DVD. Why is that? And how can I change it? How do  I get the computer to install Mac OS X from the DVD, and not Time  Machine?

---

### Post by Anon7-2521 on 2011-04-19
You might want to ask this on an Apple forum. I've been using OS X for years and have never had this problem before. Did you try putting the DVD in and holding down the option/alt key on boot?

---

### Post by cfr42 on 2011-04-20
So you can boot from the DVD?

Is the drive you use for Time Machine connected? If so, have you tried disconnecting it before booting from the DVD?

---

### Post by nl4m on 2011-04-25
^it's a laptop. The drive is build in. From the official DVD I can only choose the "Time Machine" option. 

If I try to boot from the generic Mac OS X DVD it freezes... Does not get passed the screen you get when you hold down the "Option" key at start up...

---

### Post by handy on 2011-04-25
Holding down "c" when you start the machine doesn't allow you to boot the DVD?

If the DVD is not physically damaged then I would talk to your nearest Apple store, hopefully where you bought it & ask them what's going on.

---

### Post by DogMatix on 2011-04-26
+1 for holding down the c key at startup

---

### Post by pauljwells on 2011-04-26
Is it an upgrade DVD not a full installer?

---

### Post by _mario_ on 2011-04-27
> **nl4m said:**
> I cannot install Mac OS X on my MacBook. When I boot from the DVD the  only option I get is to install the OS from Time Machine. I cannot do a  clean install from the DVD. Why is that? And how can I change it? How do  I get the computer to install Mac OS X from the DVD, and not Time  Machine?

if this is an official installation disc shipped with your machine, there might be another problem: afaik, the OS X installer refuses to install on disks, that aren't partitioned with the GPT partitioning scheme, don't contain an EFI system partition, or don't have at least 128 MiB of free space after the system partition. this is what OS X's disk utility sets up by default. otherwise the volumes don't show up at all.

ciao,
Mario

---

