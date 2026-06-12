---
title: "What does this mean??"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by hempa on 2007-02-22
i wrote: sudo aptitude upgrade in the terminal and got this

armcandy@armcandy-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

what i wonder is; what does: Need to get 0B of archives. After unpacking 0B will be used. mean??

---

### Post by Maestro23 on 2007-02-22
Very simply, nothing needed to be upgraded and nothing was upgraded.

---

### Post by louis_nichols on 2007-02-22
It means all your packages are up to date and there are no newer ones to install. That's a very good thing! :)

---

### Post by hempa on 2007-02-22
thanks! i am new to this so i was a little confused.

---

### Post by louis_nichols on 2007-02-22
One thing, though. Usually, it is best to run 
```
sudo aptitude update
``` and then ```
sudo aptitude upgrade
```

The first command will query the servers containing information about possible upgrades and refresh that information in your system. The second command does the actual download and installation of packages that do have available updates.

---

