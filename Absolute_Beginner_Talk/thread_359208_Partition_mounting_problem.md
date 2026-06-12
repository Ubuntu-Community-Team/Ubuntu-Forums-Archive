---
title: "Partition mounting problem"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by jolger on 2007-02-11
hello there, i have a bit of a problem...
i have 2 harddisks (maxtor maxline III 250 GB)
and those are set up as JBOD (wich i still dont know what is, but it works... lol)
well i created 2 partitions in windows, and now i want to access them in linux (since all my backup data is on those two disks)

i have tried to mount every possible harddisk that is on my system, but i just cant get acces to the second and biggest partition on those two disks.

the first one wich is about 214 GB big works fine, i can get access to it and all with no problems (read only), but no matter wich sdx# i try to mount, i just cant get access to the second partition, where my most important stuff is -_-

i hope someone here can help me figure this out ^^ cya later...

/Jolger

---

### Post by taurus on 2007-02-11
Post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by click4851 on 2007-02-11
just some trivia...JBOD: Just a Bunch Of Disks RAID array. Usually used when you don't have two or more of the same disks.

---

### Post by jolger on 2007-02-12
> **click4851 said:**
> just some trivia...JBOD: Just a Bunch Of Disks RAID array. Usually used when you don't have two or more of the same disks.

yes i found out...

actually we can close this thread... since im using windows to copy my files on to two seperate harddisks...

the problem was that there was no linux driver for my hardware... as said... im using windows to transfer my files to two sepperate drives, and after that formatting the two "old" ones in ext3 or w/e, after that im going to copy the files i just backed up to those drives (ext3 or w/e)... and i should be going...


i hope whoever just read this understood most of it :P

---

