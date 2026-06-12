---
title: "Im unable to upgrade to 6.06 LTS"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by candide on 2006-07-02
when i use update manager, and try to upgrade to dapper, i get an avalanche of errors!-- such as:

[http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:) 404 Not Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:) 404 Not Found

and

W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)

Ive read a few posts about this problem, but the answers have been complex. what, essentially, must i do to fix this?
thanks

---

### Post by woedend on 2006-07-02
gksudo gedit /etc/apt/sources.list

put a # sign in front of those items (the koti ones) such as
# deb [http://koti.mbnet.fi/~ots/ubuntu](http://koti.mbnet.fi/~ots/ubuntu) breezy
# deb-src [http://koti](http://koti).......

then save...then open a terminal(or use the same one) and do 
sudo apt-get update

---

### Post by BobSongs on 2006-07-02
If you know enough about the system and were your stuff is actually located ... it's sooooo much better to wipe and install Dapper. But if you're not sure where everything is ... risk the upgrade.

---

