---
title: "errors"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by hotrodpunk on 2006-10-01
keep getting these errors coming up and dont have a clue what to do next nothing i try seems to work but i dont have much of a clue. HELP!

E: Type ‘[http://rob.pectol.com/ubuntu-firewall.md5sum’](http://rob.pectol.com/ubuntu-firewall.md5sum’) is not known on line 23 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem


This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

---

### Post by pistcivet on 2006-10-01
Looks to me like your sources.list somehow got hosed.

You can either get a new one here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Or make you own here:
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Or just post your /etc/apt/sources.list
and we'll try to figure out whats wrong.

---

### Post by hotrodpunk on 2006-10-01
legend cheers man! seems to have worked...hosed sounds bad :confused: . i tried to install a firewall and it seems to have just been the start point of my grief?

---

