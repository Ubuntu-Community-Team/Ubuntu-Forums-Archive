---
title: "Booting from live CD"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by medha on 2007-12-18
Hi!

Another newbie question, I booted from a live CD and now I want to access the root for the localhost, how do I do it? All I can see is the root for the CD.

---

### Post by taurus on 2007-12-18
You need to mount the harddrive first before you can access it.  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l <-- lower case letter l, not number 1
```

---

### Post by medha on 2007-12-18
The command give a list of the partitions, among other stuff, 
/dev/sda1...4

where sda 1, 2 are swap, and 3, 4 are linux. The filesystem, reiserfs, is on sda4.

---

### Post by mukul_d on 2007-12-18
Could you post the actual output?

---

### Post by medha on 2007-12-18
The reason I need to do this is I need to copy some information to the root@localhost from another machine, and I dont know how to access root@localhost.

---

### Post by Cypher on 2007-12-18
Strange that you have two swaps..but anyway..try the following
```

mkdir /tmp/sda4
mount -treiserfs /dev/sda4 /tmp/sda4
cd /tmp/sda4

```
Check out what's there and if that's the root, if not, you might want to mount /dev/sda3 based on what type of filesystem that is..

---

### Post by jfinkels on 2007-12-18
> **medha said:**
> The reason I need to do this is I need to copy some information to the root@localhost from another machine, and I dont know how to access root@localhost.

FYI: "root" is the name of the super user and "localhost" is a shorthand for the name of the local machine.

What exactly are you trying to do? It is very rare that you need to login as root at all. For some basic info about root and sudo, read the link in my signature about Root & Sudo.

Do you need to copy data from the liveCD to a hard disk? Do you need to copy data from one hard disk to another hard disk? Do you need to copy data across a network from one machine to another machine?

---

### Post by medha on 2007-12-18
Thanks! That worked.

I was getting a PAM failure, there were no pam file/dir in root, and so I wanted to copy them. That didnt help resolve the PAM failure error..

---

### Post by medha on 2007-12-18
I need to copy data from /etc folder in the live CD to the hard disk.

---

