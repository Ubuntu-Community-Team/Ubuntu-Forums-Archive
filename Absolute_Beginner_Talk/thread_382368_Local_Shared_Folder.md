---
title: "Local Shared Folder"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by russell.h on 2007-03-12
So I have a partition called /data which I want to use to store most of my data like movies, music, etc.

The problem is that every time I create a file or folder in there it gives whatever user created the folder the permissions to it. Then I have to go back and go to "properties" and apply the global permissions to all the files inside it, or go through and change every file individually.

Is there some way of changing the /data partition so that anything created on it will automatically have read/write permissions for everyone?

Thanks,

Russell

---

### Post by shareMenaPeace on 2007-03-12
Do you mean everyone or your ubuntu default user?

for the default user its like (If the partition has a mount point in /media called data)

```
sudo chown username:username /media/data
```
username is your default ubuntu username. This assigns user and group owner.

For all i think this could work

```
sudo chmod 777 /media/data
```
This gives read/write to everybody ...
Im not 100% sure if this is the right way maybe wait for another opinion =P

---

### Post by andreas64 on 2007-03-12
...and maybe it's a good idea to change the umask for that folder - so the correct permissions for all new files are set.

Andreas

---

