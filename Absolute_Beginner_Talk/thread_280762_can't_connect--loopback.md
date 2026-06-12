---
title: "can't connect--loopback?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by benner on 2006-10-20
I had kubuntu running with no problems but decided to switch to the edgy edubuntu beta release last week.  i can no longer connect to the internet.  i used the same install cd on another machine (both were connected when i ran the installer) and it had no trouble.  it connected with no changes to any settings.  thi one is in my classroom and is connected with 3 other machines through a switch.  one is a windows machine and it is fine.  another is running kubuntu and it is also fine.  the 2 that i just installed edubuntu on can't connect.  they can't ping the gateway, dns or anything.  the network guy in my school took a look and, while he is as new to linux as i am, suggested that it looks like the loopback device is running the show and might need to be disabled or something.  the eth0 appears and it is set up for DHCP and all of the settings are exactly as they were when the machine had Kubuntu running last week.  is there something i am missing?  please dumb down your answers for me a little.  i am still a new b.  thanks.

---

### Post by Tyrel on 2006-10-20
I am having the Same Problem Friend.  Sometimes it works (fast) sometimes it works (slow) and certain sites I cant get to work at all.  But when I boot up into XP Everythings works great.  :confused: I am really having trouble troubleshooting the problem.

---

### Post by benner on 2006-10-20
thanks.  actually, it isn't that it works sometimes and not others.  there is no connection to the network.  there is no ip address.  it only sees itself.  i tried several ethernet cables and i know that isn't the problem.  when i installed it, it saw enough that the dns and gateway were automatically identified, but whem i ping those machinese, they aren't seen.  there is no network connection.  any suggestions?

---

### Post by haack on 2006-10-31
I have a similar problem with the network. I have /var on its own partition and therefore i got an error in early boot after switching to the real root.
/var is not mounted at this time but some scripts wanted to access the /var/run directory... In this case /var/run/networking. 
I thing, the state files couldn't created: lo and eth0 are not setting up. I must manually make ifdown lo/ifup lo and ifup eth0 after system is up...
I am not shure about the right resolution: modifing the first startup script to force /var in the right place? No idea what happend on the next update...

I think, there are more problems in the initphase and i hope that upstart finally resolves this problems. A second problem for me is ldap. udev want to get some things from ldap but the network is not yet up!

I'm not shure but i think i don't have the /var - network problem in dapper. Must look in my backups and restart the old system - if i have time..

Alfred

---

### Post by ninjasteve on 2007-11-05
This appears to have been solved in this thread:  [http://ubuntuforums.org/showthread.php?t=197874](http://ubuntuforums.org/showthread.php?t=197874)

---

