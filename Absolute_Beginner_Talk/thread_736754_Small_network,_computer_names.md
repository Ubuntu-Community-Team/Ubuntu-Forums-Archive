---
title: "Small network, computer names"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by The Titan on 2008-03-26
I have a small home network.  One computer is my workstation, named dungeon at IP 192.168.0.3.  And a server named temple at IP 192.168.0.2.  so from my workstation if i type 192.168.0.2 into the browser but if i type temple it dosent.  You will probably need the output of a command or the contents of a file.  Please let me know, thanks in advance

---

### Post by glennric on 2008-03-26
You just need to edit the file /etc/hosts and add the line
```
192.168.0.2 temple
```
on your workstation.

---

### Post by The Titan on 2008-03-26
thanks :)

---

### Post by chilinski on 2008-03-26
If you happen to have a windows machine that you want to put on the network, the hosts info is located in c:\windows\system32\drivers\etc in hosts or lmhosts (you'll see an lmhosts.sam in there; ignore it). On Windows you have to "reload" the lmhosts table when you put new entries in (you don't have to do anything in Linux). At a command prompt type: nbtstat -R 

I know you didn't ask, but someone somewhere someday will...AND they will use the SEARCH feature and actually find this.

---

### Post by The Titan on 2008-03-27
> 
I know you didn't ask, but someone somewhere someday will...AND they will use the SEARCH feature and actually find this.

Hopefully anyways... But thank you

---

### Post by Joeb454 on 2008-03-27
I've never had to edit the hosts file.

Try adding the home domain name (often HOME - MS uses...MSHOME :lolflag:)

so you could try temple.home :)

---

