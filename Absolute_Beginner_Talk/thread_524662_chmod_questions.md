---
title: "chmod questions"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by CryptiniteDemon on 2007-08-13
I've used chmod a lot for making executables, but I'm having a little trouble with it and the gnome desktop.

For instance, when i go and make say a fille "hello.cig"  a 777 file I type in

chmod 777 hello.cg


but when I go to the file and right click on the thing and go into it's permissions in the properties nothing changes at all.  It still just says read only for group and all, and then read write for the owner.

Does chmod only apply if I'm working with files in bash or is it supposed to do the same for the gui too?

---

### Post by bodhi.zazen on 2007-08-13
should work on the gui as well.

Not to ask the obvious, but are you the file owner and are you in the correct directory when you chmod ?

Is the file stored on a FAT or NTFS file system ?

---

### Post by CryptiniteDemon on 2007-08-13
File is on the ubuntu partition, I am the owner and yes I'm in the correct directory.

---

### Post by mali2297 on 2007-08-13
I made a simple test.

```

touch hello
chmod 777 hello
ls -l hello

```

That gave me:
-rwxrwxrwx 1 ...my user name etc... hello

But when I checked in the file browser, in my case thunar in xfce, it was recognized only as a textfile. Does this also happen with real (non-empty) executables?

---

