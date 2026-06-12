---
title: "tri booting imac..."
date: 2008-02-06
forum: Apple PPC Users
---

### Post by thespottedelf on 2008-02-06
I have an imac and i need to have both osx and os 9.

I'm trying to figure out how to install ubuntu onto my biggest partition that is in the unix file system right now... i also have hfs+ with osx installed and after i'm done with ubuntu i'll install os 9 on my hfs partition.

What do i need to reformat the unix file system into for ubuntu?

---

### Post by ssam on 2008-02-07
if you can install ubuntu last. it will save you having to reinstall yaboot (the bootloader).

also don't worry about the unix filesystem that mac os x talks about. it is not very compatable with linux. its best to get the mac partitioner to leave unallocated space, and then get the ubuntu installer to make the linux partitions.

---

### Post by thespottedelf on 2008-02-07
thank you (its working on it right now)

now do i need to install grub or something to manage which volume to boot from?  Or could i use the old hold down option when i boot?

---

### Post by ssam on 2008-02-07
the ubuntu install installs yaboot, which does pretty much the same job as grub.

---

### Post by thespottedelf on 2008-02-07
its working great yaboot isn't that bad :D

now i can still play my old games :D

---

