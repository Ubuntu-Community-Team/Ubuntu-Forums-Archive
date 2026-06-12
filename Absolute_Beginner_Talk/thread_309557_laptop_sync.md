---
title: "laptop sync"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2006-11-29
Hello, 

I just bought a new laptop yesterday, and am in the process of setting it all up with Ubuntu Edgy :D 

When I was in England, where I worked, the laptops all had a script on them that when they connected to the LAN, it downloaded all the patches etc, 

I was wondering if it is possible to do something similar, whereby when I connect to the network at home, either wirelessly or via ethernet, it copies all the specified folders and directories to my desktop? 

Pretty much a daily backup to my desktop really. 

I am assuming I just need to write a script that gets run on start up, and checks if the network connection is present... actually, my laptop doesnt connect to the network on startup, is there a way to do it so it backs up when first connected to the network?

Any help and advice would be appreciated

Thanks

Patrick

---

### Post by TerryHowe on 2006-11-29
There is a GUI tool that does file syncs, I loaded it up to do palm syncs, but I don't recall the name.  Might try searching palm or sync in synaptic.

If you go the script route, the lftp command might be where it is at.

---

### Post by xolot1 on 2006-11-29
rsync is easy to use as well. 
i think its on the order of 
```
rsync {what you want copied} {where you want it copied to}
```

this may not be the most efficient way of doing this, but you could try to write a bash script along the lines of:

runs at startup
pings some server until its successful
when its successful,
runs rsync on the folders you want updated
then exits

good luck

willi

---

### Post by jpkotta on 2006-11-29
Unison: 

[https://help.ubuntu.com/community/Unison](https://help.ubuntu.com/community/Unison)
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

```
sudo aptitude install unison-gtk
```

---

### Post by ozPATT on 2006-11-29
> **jpkotta said:**
> Unison: 

[https://help.ubuntu.com/community/Unison](https://help.ubuntu.com/community/Unison)
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

```
sudo aptitude install unison-gtk
```

ooh, that looks like just the ticket.... will have a look into that thanks

---

