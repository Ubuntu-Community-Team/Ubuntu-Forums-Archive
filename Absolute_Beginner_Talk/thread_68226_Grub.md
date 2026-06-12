---
title: "Grub"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by lavarock09 on 2005-09-22
Hey,

How do I edit Grub etc?

Thanks

Lavarock

---

### Post by KingBahamut on 2005-09-22
BUM - Boot Up Manager 

[http://ubuntuforums.org/showthread.php?t=42129](http://ubuntuforums.org/showthread.php?t=42129)

---

### Post by lavarock09 on 2005-09-22
I'm not very good at all this,

How do I install it?

---

### Post by KingBahamut on 2005-09-22
sudo apt-get install bum

---

### Post by lavarock09 on 2005-09-22
when I do that I get the error,

> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package bum


---

### Post by thomax on 2005-09-24
[QUOTE=lavarock09]when I do that I get the error,[/QUOTE]

Same for me :(

---

### Post by PsyberOneZero on 2005-09-24
It's in the Universe section (At least in breezy) try adding universe and/or multiverse to sources.list or in the synaptic repository list.  
```
System->Administration->Synaptic Package Manager 
Settings->Repositories
Select the "Ubuntu 5.04 (binary) entry -> click edit
Add universe and multiverse to the sections area
reload
```
That should work

---

