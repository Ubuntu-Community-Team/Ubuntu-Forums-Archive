---
title: "ntfs-3g = slow, read only ..."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-04-28
Using Ubuntu Feisty Fawn:
I installed ntfs-3g in order to access my NTFS partitions. 
I have the following problems:

- the File Browser is slow when I try to browse an NTFS partition - the screen turns gray and takes maybe 30 seconds to move to the next directory.  I can go to a shell prompt and it is quick and responsive but when I try to remove an  NTFS file -- I get "cannot remove 'filename' : Read-only file system.

- I had ntfs-3g working in Ubuntu 6.10 but cannot get it to work now with Feisty.

Any help would be appreciated.

Thanks

Carl

---

### Post by Najand on 2007-04-28
it's a known issue. Your disk is close to full, highly fragmented and it may have been formatted/converted to use a too small cluster size. 
Install it again using universe repository (Universe repository must be enabled!)
```

sudo apt-get install ntfs-3g

```

---

### Post by cwmoser on 2007-04-28
What is "Universe Repository"?  I've seen the phrase but not sure what it is.

Thanks

Carl

---

### Post by Najand on 2007-04-28
Go to System -> Administration -> Software Sources
And check all options on the page with "ubuntu software" tab. You may also select the closest mirror site to you.

---

