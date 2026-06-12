---
title: "Copying files from desktop to root?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-08-27
[IMG]http://i14.tinypic.com/4ztzvo9.jpg[/IMG]

---

### Post by dwhitney67 on 2007-08-27
That's because you do not have "root" privileges.  Um, is there any particular reason that you find necessary to write to that directory?

There is a reason for everything in Unix/Linux.  That directory is owned by root so that the average joe-user does not add or delete things from it.

---

### Post by Perfect Storm on 2007-08-27
```
cd <distination>
sudo mv <file> <distination>
```

put a * after mv instead of file if you want to move all.

---

### Post by raijinsetsu on 2007-08-27
You shouldn't do that. If you're trying to get your windows installed in Cedega or Wine, then you need to copy the windows directory to your "~/.wine/drive_c/" directory.

---

### Post by Zalbor on 2007-08-27
You don't have permission because you only have permission to write in your home folder. If you want to do this, use a terminal and type "sudo cp -R ~/Desktop/win32 /".
But be careful: Why do you want to do this? It's best not to write anywhere outside your home folder unless you really have to, and I don't see any reason to do this. So you'd better not. if you tell us what you're trying to do, perhaps we can help better.

---

