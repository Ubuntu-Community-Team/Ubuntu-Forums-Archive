---
title: "installed package ---how can i move it?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by williamburn on 2007-06-15
So here is my dilema, i downloaded a package, unpacked it, and isntalled it.  I now have the package with a lock on my desktop --- is there a way to move that so its not cluttering up my desktop?  I probably should have, in the future, unpacked that program to a different directory.

I am very new to linux and dont quite understand the file hierarchy just yet.  

Be gentle and thanks.


FYI - SADMS-2.0.10 is on the desktop with a LOCK

---

### Post by drs305 on 2007-06-15
If you want to delete it:
```
sudo rm ~/Desktop/filename
```
Note: to remove an entire directory instead of a single file, you add  -r or -R after the rm
```
sudo rm -R ~/Desktop/directory_name
```

If you want to move it:
```
sudo mv ~/Desktop/filename new_location/filename
```

Since you said there was a lock on the filename, I am assuming it is owned by root. That is why you use the sudo command. If you own the file, you don't need to preface the command with sudo.

---

