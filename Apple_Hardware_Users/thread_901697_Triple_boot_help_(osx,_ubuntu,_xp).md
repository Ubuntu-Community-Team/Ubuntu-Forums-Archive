---
title: "Triple boot help (osx, ubuntu, xp)"
date: 2008-08-26
forum: Apple Hardware Users
---

### Post by Jount on 2008-08-26
Hi

I need some help triple booting a mbp 3rd gen. Right now I am double booting - leopard and heron. I now want to throw xp into the mix, but I'm worried I'll screw something up. 

The directions i've read for 3booting all say install xp before ubuntu, so thats making me nervous. I'm still new to ubuntu. 

Current partitions if it helps:

/dev/disk0
#:    TYPE NAME      SIZE       IDENTIFIER
0:  GUID_partition_scheme   *111.8 Gi   disk0
1:  EFI                      200.0 Mi   disk0s1
2:  Apple_HFS Macintosh HD   100.9 Gi   disk0s2
3:  Microsoft Basic Data       9.8 Gi   disk0s3
4:  Linux Swap               953.7 Mi   disk0s4

Any advice on what to do? I really don't want to reinstall any osx if possible, but I can easily reinstall heron if needed. Thanks!

---

### Post by Jount on 2008-09-01
[help please?]

---

### Post by cyberdork33 on 2008-09-01
just delete your Ubuntu partitions, and create your new ones in place of them.

delete partitions 3 & 4,

create:

[LIST]
[*]ubuntu root partition (sda3)
[*]xp partitions (sda4)
[*]linux swap (sda5)
[/LIST]
If you need more space then you currently have then you have to resize your OS X partition first.

---

