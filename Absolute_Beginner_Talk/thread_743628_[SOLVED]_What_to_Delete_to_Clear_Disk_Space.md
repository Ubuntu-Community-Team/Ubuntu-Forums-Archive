---
title: "[SOLVED] What to Delete to Clear Disk Space?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by insineratehymn on 2008-04-02
Thats a loaded question, friend.

I would start in any users that aren't root.
Look for media files; jpgs, mpegs, mp3s, gifs, etc...

In unix, there really isn't much of a file extension to look for, so your out of luck there.
I would make friends with the file command to see what everything is.

---

### Post by ByteJuggler on 2008-04-02
Check if there's stuff under /tmp that you can safely delete, usually it's all deleteable, although some of it may be currently in use.

Also check /var/log/* for old log file arhives that can be deleted.

---

### Post by wolfen69 on 2008-04-02
for starters
```
sudo apt-get clean
```
```
sudo apt-get remove
```

---

### Post by Jim D v2.0 on 2008-04-02
I know this seems obvious but have everyone that has logged into this computer (not just you) empty the trash container.

---

### Post by nhandler on 2008-04-02
> **Jim D v2.0 said:**
> I know this seems obvious but have everyone that has logged into this computer (not just you) empty the trash container.

If he has root access (which he does), he can empty all of the trash cans himself. The trash is stored in ~/.Trash. That means it is a hidden directory named ".Trash" in every user's home directory. Depending on the number of users, you can either manually delete this folder, or you can create a script to do it for you.

I also suggest using the disk usage analyzer which I believe came installed on gutsy. This will show you what folders/files are taking up a lot of space on the computer.

---

