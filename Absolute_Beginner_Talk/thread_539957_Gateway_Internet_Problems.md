---
title: "Gateway Internet Problems"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by ericsaxalto on 2007-08-31
I recently purchased a Gateway MT6705 laptop.  I've been getting some advice on trying to get internet access.  I'm running Dapper Drake and even though it recognizes the ethernet card and the wireless I can't connect using either.  It works in Windows but my machine isn't allowing me to get into windows right now.  The hardware is made by Marvell Technologies.  It is a Marvell 88E8053 PCI-E Gigabit Ethernet Controller.  I found a driver on NDISwrapper: yk51x86.inf - but I don't know how to enter that into my terminal.  Also, whenever I enter the command "sudo -i" to gain root access it will not accept any typed characters in the line for the password.  I'm not sure if what I've found is useful, but if someone can help me to decipher and figure out what I need to do I would greatly appreciate it.  :confused:

---

### Post by diatribe on 2007-08-31
it accepts the characters it just doesnt display anything signifying you typed

---

### Post by chamberlain2006 on 2007-08-31
NdisWrapper may work for your wireless, but not for your wired connection.  There is a bug report [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87884](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87884) that may help.

---

