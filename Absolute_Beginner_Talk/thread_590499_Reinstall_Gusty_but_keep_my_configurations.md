---
title: "Reinstall Gusty but keep my configurations?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-10-24
I've got some problems that seem to be pretty isolated, and no one really seems to know how to fix them.  So I figure the easiest solution would be to just reinstall Gusty, and go from there.  The thing is, if I had to go back and redo all the changes I've made, it would probably take me the better part of a week.  So is there folder or something that has configurations stored that I could backup so I wouldn't have to replace everything?

Thanks.

---

### Post by rsambuca on 2007-10-24
All of your config files are in hidden directories on your /home.

---

### Post by Yes on 2007-10-24
So if I just backed up my /home partition, and then replaced my new /home partition with the backup, I would have most of my old configurations?  Is that for just programs, just Ubuntu, or both?

Thanks.

---

### Post by rsambuca on 2007-10-24
Should be for almost everything.  If you view your /home folder, check the "View Hidden Folders" box.  You will see the folders containing all of your programs' config files.

---

### Post by Yes on 2007-10-24
Great, thanks.

---

### Post by taurus on 2007-10-24
Applications -> Accessories -> Terminal
```
ls -la ~
```

---

### Post by Yes on 2007-10-25
Is it possible when I repartition the hard drive when I install it to have it not repartition the /home partition, so I don't have to back everything up, and then copy it all back?

---

### Post by mivo on 2007-10-25
Yes, if /home is on its own partition, you only have to assign the mount point. Make sure you **do not** check the "format" box next to the partition. You only want / and swap formatted. Works like a charm.

---

### Post by freetonik on 2007-10-25
If I do like that - just mount /home partition - even my compiz-fusion options and AWN will be working after reinstall? What about hundreds of libraries installed?

---

### Post by mivo on 2007-10-25
Only personal files (songs, videos, mail, notes, Wine programs, etc.) and settings are stored in /home (this includes settings for Compiz). Libraries and applications will need to be reinstalled.  See [this post]("http://ubuntuforums.org/showpost.php?p=3620306&postcount=8") for information on how to get a list of installed software/libs and how to install them again painlessly.

---

### Post by freetonik on 2007-10-25
Thank you
Well, actually I don't need to reinstall the system, I only need to make /home and / partitions bigger. Will it be okay if I just make them bigger using Acronis Disk Director Suite?

---

