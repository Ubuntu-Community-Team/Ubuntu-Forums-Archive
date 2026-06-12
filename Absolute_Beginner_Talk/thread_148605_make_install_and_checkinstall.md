---
title: "make install and checkinstall"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by icyisamu on 2006-03-22
Lets say I have a software that isn't in the respository and I have to manually compile it myself.

I will first do a

```
./configure
make
```

Then I can either choose to use **make install** and **checkinstall**.

From what I read, **checkinstall** will create a deb package and make it available in  the package manager.

What about **make install**? How do I remove software installed via it? Do I just have to delete the directory where I install it?

Thanks in advance :)

---

### Post by bluevoodoo1 on 2006-03-22
Pretty sure you "cd" to the program's folder and run "make uninstall" (I always use checkinstall)

---

### Post by xtacocorex on 2006-03-22
If you use make install, you need to keep the source directory and then use make uninstall. This works well, but I've realized the power of checkinstall.

Once you compile with checkinstall, you can keep the .deb file and delete everything else. You can easily back up all the programs you compile yourself so if you have to reinstall the os, you can easily install your .deb files without having to redownload the source.

---

### Post by icyisamu on 2006-03-22
Thanks alot. I couldn't remove installed via make install. Now I can remove it and install it via checkinstall.

---

