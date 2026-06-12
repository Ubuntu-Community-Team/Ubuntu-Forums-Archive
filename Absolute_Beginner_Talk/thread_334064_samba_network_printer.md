---
title: "samba network printer"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by monk_rock on 2007-01-08
I have three computers one with xp another with win 2000 pro and ubuntu. The windows machines are ok. The linux machine can see both of them. It can open xp and see a shared folder. It can't open the 2000 pro machine. I mainly want to be able to set up the linux machine to use the win2000 pro's printer. can anyone help me?

---

### Post by tagra123 on 2007-01-08
Is the shared folder on the 2000 machine  opening from ubuntu?

What printer model?

---

### Post by scrooge_74 on 2007-01-08
Are you using Firestarted to manage your iptables? If so this could help you with setting up the connections to the other machines

[http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)

---

### Post by monk_rock on 2007-01-08
> **tagra123 said:**
> Is the shared folder on the 2000 machine  opening from ubuntu?

What printer model?

no i can't access win 2000 at all. all i can do is see it. i can access xp though. i can run smbclient -L name -N on the xp as well and I can't do it on the windows 2000 machine. the printer is a hp photosmart 7550. i already aquired the linux driver for it.

---

### Post by monk_rock on 2007-01-08
> **scrooge_74 said:**
> Are you using Firestarted to manage your iptables? If so this could help you with setting up the connections to the other machines

[http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)

I don't know what firestarted is at all.

---

### Post by oyvindaa on 2007-01-08
[Here's](https://help.ubuntu.com/community/NetworkPrintingFromWin2000) a method sorting it out without the use of Samba.

Maybe that'll work for you? :)

---

### Post by scrooge_74 on 2007-01-08
> **oyvindaa said:**
> [Here's](https://help.ubuntu.com/community/NetworkPrintingFromWin2000) a method sorting it out without the use of Samba.

Maybe that'll work for you? :)

I dont think this will help him because the printer is not in the Ubuntu PC is on the win2000 Pc

---

### Post by oyvindaa on 2007-01-08
Hm.. that's right. Sorry.

---

### Post by tagra123 on 2007-01-08
Are the domain names all set to MSHOME or WORKGROUP ?


I believe samba defaults to WORKGROUP, but 2000 may be set to MSHOME.

By the way, you can check in System-Administration-Networking and clicking on the general tab

---

