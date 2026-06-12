---
title: "Local Network"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Orthodox_Celt on 2007-04-20
Hi,

I kind'a have this problem wih my local network in company where I work.
Recently I switched to ubuntu and running 6.06 LTS, but all other computers in my ompany are on ms windows xp.

I see them all from my computer (using samba) and I can move change etc.. shared folders and files from their computers but noone can come to my comp.

When they try to do that dthey are asked for password, and when they typeit they still can;t come in....

Where is the problem? :confused:

---

### Post by mendingo84 on 2007-04-20
Hi,

it is a common fact that windows can't detect ext3 partitions. no problem in the other way though. i think there is some software you can install on windows machines in order to detect you ext3 linux partitions. or you could make a fat32 partition and place the files you want to share there. fat32 because both windows and linux can read/write from /toit easilly...you know that linux can only write to ntfs partitions with help from some special package which i don't know :) . good luck! :popcorn:

---

### Post by Orthodox_Celt on 2007-04-20
Thanks, I'll try that :popcorn:

---

### Post by xyz on 2007-04-20
This may help:
[HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method)]("http://ubuntuforums.org/showthread.php?t=217009")

---

### Post by bullgr on 2007-04-20
after you setup your disks/files/folders in samba to be able to read and/or write the other network users,
you must setup iptables to pass thru samba.

iptables is the "firewall" in ubuntu and in a default ubuntu install all the incoming ports are closed 
(the outgoing ports are open, it is supposed that you know what you do).

so, you can see the other winblows shares but they can't see your's because iptables don't let then thru.
just open the port for samba in iptables and all be done.

one solution is to use firestarter (gui for iptables) and the other solution is to use script's from the command-line.
the choice is your's...

---

