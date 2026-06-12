---
title: "deleting tmp deleted half my home directory"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by marn on 2007-11-09
In the process of updating to gutsy I wanted to clear some disk space. I went (via the GUI) to the tmp directory, marked everything and hit delete. 

As well as getting a lot of error messages (no permissions etc) it also seems to have deleted half of my home directory! :(

Can anybody tell me why? And maybe a better way of getting rid of the temporary files :)

---

### Post by 3rdalbum on 2007-11-09
Sorry that things have gone pear-shaped for you; I don't know why deleting files from /tmp would have deleted things from your home directory.

> **marn said:**
> And maybe a better way of getting rid of the temporary files :)

Reboot! They are all deleted on shutdown... or startup... for obvious reasons, it's hard to know which :)

---

### Post by marn on 2007-11-09
thanks for your sympathy. I now know that the tmp file is emptied on reboot. Luckily I had a backup, so all that I lost was not important. Still, it is a bit disconcerting when things like that happen

---

### Post by ByteJuggler on 2007-11-09
Deleting stuff from one location won't delete stuff from another location, so there must be more going on here than meets the eye. 

You can delete stuff from the command line using the "rm" command.  If you use the "-rf" switch it will "f"orcibly and "r"ecursively do this. So for example, 

```
rm -rf /tmp/*
```

Will delete or attempt to delete everything in /tmp.  You can increase the power of the command by adding "sudo" in front, to run it as administrator.  

Be however ***_very very careful _***with the "rm -rf" command, a slip of the finger can potentially cause trouble.  "rm" doesn't ask for confirmation, so it will just do what it's told...

---

