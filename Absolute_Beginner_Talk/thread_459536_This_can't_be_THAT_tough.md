---
title: "This can't be THAT tough"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by gantww on 2007-05-30
I'm trying to get my fileserver going. It has a second hard driver, which is mounted and contains a folder with all my MP3s. I can read the folder from that machine. On a second machine, I browsed out on the network to that location, saw my shared directory and tried to copy from it into my home folder. It won't copy. There is no error message or anything - it just acts like I didn't do anything. Both machines have samba on them.

I also tried copying by doing:
gksudo nautilus

and then browsing to the directory. Still no luck. I did, however, see the following messages in the terminal:

Couldn't get main dbus connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Couldn't get main dbus connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


Any ideas?

---

### Post by Ocxic on 2007-05-30
try using NFS instead of SAMBA it's a native linux networking filesystem, and would prolly workout better.


check firestarter and makesure you have the correct ports opend, on both computers.

---

### Post by gantww on 2007-05-30
No luck. Now I can't even browse the samba shares.

---

