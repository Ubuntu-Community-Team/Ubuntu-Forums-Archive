---
title: "Rrrar."
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-10-18
I have downloaded unrar, but I still can't seem to open any .rar files.  Is there a better program to do it?

---

### Post by PriceChild on 2006-10-18
How are you trying to open them?

---

### Post by OptimusPrime on 2006-10-18
Just by clicking on it?  I have tried various programs to open it, but just gives me this:

Archive type not supported.

---

### Post by PriceChild on 2006-10-18
ok could to try it in the terminal instead for me? Navigate to where the file is (cd /path/to) then:
```
tar -xf <<name here>>
```or if it has a gzip extention (.tar.gz)
```
tar -xzf <<name here>>
```

---

### Post by OptimusPrime on 2006-10-18
It doesn't do anything, it just goes down a line and gives me this: >

---

### Post by PriceChild on 2006-10-18
Could you paste from the terminal to here to let me see exactly what's going on?

also do a "ls" before so i can see the contents of the folder please :)

---

### Post by CatKiller on 2006-10-18
> **OptimusPrime said:**
> I have downloaded unrar, but I still can't seem to open any .rar files.  Is there a better program to do it?

```
sudo aptitude install rar
```

You may need to enable the other repositories first.

---

