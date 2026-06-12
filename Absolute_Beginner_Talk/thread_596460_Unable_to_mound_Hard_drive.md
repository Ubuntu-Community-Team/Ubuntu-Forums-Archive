---
title: "Unable to mound Hard drive"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by triplechuck on 2007-10-29
What does it mean when i try to access a hard drive  and it says unable to mount drive... and how can i fix that

---

### Post by Ralphie on 2007-10-31
they might be NTFS -- are they?

if so you can mount them automatically by installing ntfs-config (in terminal type:

```
sudo apt-get install ntfs-config
```

when finished installing that, you can type:

```
gksu ntfs-config
```

in the same terminal window, to mount your drives. they should now show up on the desktop..... this is assuming they are NTFS partitions-- if they were HDDs in a windows xp box there is a good chance they are NTFS.

more info on mounting things:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28mount%29](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G?highlight=%28mount%29)

as a side note, you are in the wrong area for the question :) 

hope this helps

---

### Post by frafu on 2007-11-13
Hello, 

I am moving this thread to a more appropriate forum. 

Have a nice day. 

Francesco

---

