---
title: "servers list invisible in amule"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by ronamin on 2008-02-05
Hi, in amule i cannot see the servers names while server list is populated
i can connect to servers - but i cannot know which one cause they not shown
please advise
Ubuntu 7.10

---

### Post by Hallvor on 2008-02-05
The servername should be on your bottom right on the screen.

[http://www.amule.org/scr/amule-scr-server-ed2k.png](http://www.amule.org/scr/amule-scr-server-ed2k.png)

---

### Post by ronamin on 2008-02-06
this is how it's look a on my ubuntu.
servers exists on the list because the area responding to clicks by "connecting to server"
but they are not shown

---

### Post by ronamin on 2008-02-06
ok. it almost working!
the language of the amule was set to default -system (hebrew)
when i change it to english - i see the servers! :)
but still missing the columns :(

---

### Post by Hallvor on 2008-02-06
OK. It doesn`t really matter if some columns are missing as long as the other columns (e.g. in search) are working like they should. Servers aren`t that important anyway, since they are only needed to bootstrap KAD.

But it seems you are connected to a bullsh*it server, and that you are firewalled. Delete your servers, remove the update serverlist options under preferences>servers and add a few servers from a reliable source. You should also open ports in iptables. It is easily done using the command line.

---

