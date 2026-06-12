---
title: "external hard drive problem......ntfs"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-22
hello.
ive just re-installed fiesty (had to wait for a new hard drive) anyway im trying to get my external drive to work, that is to say work so that i can read and write to the drive.
ive installed ntfs-config etc etc and ive got the option to enable write support for an external device, however it doesnt enable anything, i still cant write to the drive or move folders etc.
i install ntfs from synaptic (used to use automatix but found it to cause problems) 
any help will be appreciated.
cheers

---

### Post by Borzo on 2007-05-22
install ntfs-ng

---

### Post by taurus on 2007-05-22
> **Borzo said:**
> install ntfs-ng

ntfs-**3**g & ntfs-config

---

### Post by Inxsible on 2007-05-22
If you already have ntfs-3g installed, it could be a permissions issue
 
```

sudo chown -R <your-username> <drive-path>

```
 
Assuming your username is technoMole and drive path as /dev/sdb1
```

sudo chown -R technoMole /dev/sdb1

```

---

### Post by techno-mole on 2007-05-22
cheers for the help.
managed to fix it myself in the end, i had to put the drive onto a windows pc and use the safely remove hardware option then put it back onto ubuntu and it worked fine.
cheers again.

---

### Post by Inxsible on 2007-05-22
Glad to hear !!! :)

---

### Post by Mr.Beast on 2007-05-22
> **techno-mole said:**
> cheers for the help.
managed to fix it myself in the end, i had to put the drive onto a windows pc and use the safely remove hardware option then put it back onto ubuntu and it worked fine.
cheers again.

I have had a similar error message on this isssue, so I'll try this fix as well.  Cheers for the info :p !

Just on another point, does anyone know WHY this may happen, is there a flag set on the drive in some way?

Just interested in the mechanics of this.

---

### Post by techno-mole on 2007-05-22
i dont know why it does this, but thinking about it i should have remembered from when i had edgy installed, you had to download all the ntfs files and such like and then once it was all on and sorted you had to then unmount the drive and then stick it on a windows system and do the safely remove bit, then put it back on ubuntu and run ntfs-config and it would work like a charm.

---

