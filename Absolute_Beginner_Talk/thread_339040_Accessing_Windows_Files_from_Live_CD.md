---
title: "Accessing Windows Files from Live CD"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by brainiac8008 on 2007-01-15
Hi,

I have brought a live cd of Ubuntu 6.06 Dapper Drake to a friend's house. I have started up the disc before Windows and it runs beautifully.  I am wondering though how I can access files on the hard drive (within Windows).  I know that when you install Ubuntu that it says "hda1" and you can access it, but I just want to look at the files with the live cd.

--Noah

---

### Post by Tomosaur on 2007-01-15
If the hard disk has not been automatically mounted, you can do this:
Open up a terminal, and type the following commands:
```

mkdir windows
mount /dev/hda1 ./windows

```

You should now change directory to the newly created windows folder, using either the terminal or the file browser, where you should be able to browse around the windows files.

---

