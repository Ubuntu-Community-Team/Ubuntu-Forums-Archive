---
title: "mounting problem"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Unlockitall on 2007-02-14
i have some music on a cd, so i thought id try to listen to it in xubuntu, and copy the files to the computer, but when i put the disk in, nothing happens. so i dont panic i open up terminal and type > sudo mount /dev/cdrom and i get a reply
> mount: No medium found
any suggestions?

---

### Post by taurus on 2007-02-14
What's the output of this command from a terminal?

```
dmesg | tail
```

---

### Post by tronica on 2007-02-14
for me its always 

> mount /media/cdrom0

---

### Post by Unlockitall on 2007-02-14
i get alot of numbers and letters

---

### Post by Unlockitall on 2007-02-14
tronica, i tried it
> command not found

---

### Post by Unlockitall on 2007-02-14
bump

---

### Post by Unlockitall on 2007-02-14
another bump

---

### Post by Unlockitall on 2007-02-14
please help

---

### Post by Unlockitall on 2007-02-14
i cant access the internet until i sort out the mounting problem, so can anyone help me please?!?!?!?!?!?!?!?!?!?!?!?!?

---

### Post by Dod_basim on 2007-05-18
same ploblem, bump.

when i ask for [COLOR="Red"]sudo mount /dev/cdrom[/COLOR] or [COLOR="Red"]sudo mount /media/cdrom0[/COLOR] it get this output
```
Block device /dev/hdb is write-protected, mounting read-only
wrong fs type, bad option, bad superblock on /dev/hdv.............

```

---

