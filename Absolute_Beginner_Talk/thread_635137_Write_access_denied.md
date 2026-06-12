---
title: "Write access denied"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by vasanaditya on 2007-12-08
Hey
I'm using a 500gig external  hard-disk (FAT32) ... i'm not able to write to the hard-disk 
how can i change this ? 
any help appreciated

---

### Post by dracker on 2007-12-08
There is a way to mount partitions and enable write privileges, but I don't know it... someone will come with help for you, for the moment you can open a terminal and write

```

$ gksudo nautilus

```

put your password in it and then you can navigate to /media/YourHDD, this way you can write in the HDD.

---

