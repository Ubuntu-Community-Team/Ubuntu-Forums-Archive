---
title: "Simple Dapper-Dapper networking"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by wombat20 on 2006-06-19
Well it should be simple.  It worked Windows-Breezy previously.

Both machines are connected (physically) to a Connexant 4 port router and both are getting internet access from said router, no problems there.

However, they don't seem to be seeing each other.  I've shared folders on each machine and tried to look at them through Places -> Network Servers.  I get a "Windows Network" icon, which seems to contain nothing at all.

Surely it should be trivial for two Ubuntu machines on a wired network to talk to each other?

Any ideas appreciated.  :cool:

---

### Post by PhilOSparta on 2006-06-19
Have you tried samba or nfs ?  Samba works pretty well.  NFS has given me problems on access via maching name only, but if you are using static IP addresses you shouldn't have any problems.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by wombat20 on 2006-06-20
Thanks for that, Samba seemed to work a lot better for me than NFS.   :)

It's handy that it gives you the option to add one or both of these when you first open the shared folders option, but it would be nicer if you still had the option to add samba later from the same dialogue rather than going through Synaptic.

---

