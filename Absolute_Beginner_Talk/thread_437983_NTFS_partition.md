---
title: "NTFS partition"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by micfreedom on 2007-05-09
I have a external drive problem (WD My Book Essential) not recognized by Windows XP.I saved my Documents on this external drive. In ubuntu, becauze it is a NTFS file, I cannot open it. I have followed some instructions from the forum to copy the data in the home directory, but it still gives me no permission to open the data, sayihng that "You are not the owner, you caanot change permissions"

I've read in another part of this forum that if you change the NTFS file into EXT3 file ubuntu would be able to read it. 
1) is it possible to change afile like my saved file from Windows ihnto an EXT3 file
2)How can I transfer the data from that file into a new ubuntu file?

---

### Post by Inxsible on 2007-05-09
> **micfreedom said:**
> I have a external drive problem (WD My Book Essential) not recognized by Windows XP.I saved my Documents on this external drive. In ubuntu, becauze it is a NTFS file, I cannot open it. I have followed some instructions from the forum to copy the data in the home directory, but it still gives me no permission to open the data, sayihng that "You are not the owner, you caanot change permissions"
 
I've read in another part of this forum that if you change the NTFS file into EXT3 file ubuntu would be able to read it. 
1) is it possible to change afile like my saved file from Windows ihnto an EXT3 file
2)How can I transfer the data from that file into a new ubuntu file?
 
You should be able to read from the NTFS drives. For write access you can use the ntfs-3g. You don't necessarily have to change the filesystem to EXT3.
Go to Add/Remove and search for ntfs or ntfs-3g and install those packages.
 
you can also change ownerships as follows. Go to Applications and open up a Terminal.
and enter the following command
```

sudo chown -R <your-username> <the-partition-you-want-to-take-ownership-of>

```
 
I could give you a proper command if you tell me what is the name of the partition where you want to store your documents

---

