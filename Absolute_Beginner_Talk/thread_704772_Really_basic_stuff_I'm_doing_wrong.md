---
title: "Really basic stuff I'm doing wrong"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by NeonSamurai on 2008-02-22
Okay, so what am I doing wrong here?:

> splendid@workhorse:~/Desktop$ sudo dpkg -i oss-linux-v4.0-1013_i386.deb
dpkg: error processing oss-linux-v4.0-1013_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 oss-linux-v4.0-1013_i386.deb


Does it mean that the file I'm trying to install it into doesn't exist or that it can't recognize the file I'm trying to install? oss-linux-v4.0-1013_i386.deb is sat on my desktop and I'm trying to run it from command line.

Pretty basic I know, but sometimes linux seems so irrational to me :(

---

### Post by Crooksey on 2008-02-22
It means your probably missing the file location..

Is the file on the desktop? If not..

```

$ sudo dpkg -i /path/to/file.deb
```

---

### Post by taurus on 2008-02-22
Is that file really in ~/Desktop?  Do you see it from the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by NeonSamurai on 2008-02-22
D'oh! I'm such a pilchard! I confused a - for a _ #-o

Thanks for you help but sorry for wasting your time.

---

### Post by bwhite82 on 2008-02-22
If the path isn't the problem, it could be a simple typo. Thats where wildcards are your friend:

sudo dpkg -i oss*

---

### Post by taurus on 2008-02-22
Or just type the first couple of letters and hit the Tab key for completion.

---

### Post by SOULRiDER on 2008-02-22
> **taurus said:**
> Or just type the first couple of letters and hit the Tab key for completion.

I was gonna suggest that too, tab completion saves you a LOT of time!

---

