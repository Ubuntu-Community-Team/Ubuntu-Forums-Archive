---
title: "Intalling VMWare Workstation 5.5.2.x"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by krimson on 2007-03-11
I am trying to install VMWare Worstation 5.5.2.29772 on my ubuntu 6.10 setup, but i keep gettin the following prompt:

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.17-11

The path "/usr/src/linux-headers-2.6.17-11" is an existing directory, but it 
does not contain a "linux" subdirectory as expected.

```

then i tried:

```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.17-11-386

The path "/usr/src/linux-headers-2.6.17-11-386" is an existing directory, but 
it does not contain a "linux" subdirectory as expected.
```


i am a bit unsure as to what steps to take to remedy this...

uname -r gives me 2.6.17-11-386

thanks!

---

### Post by xopher on 2007-03-11
1. Go to /usr/src/

2. Delete the existing 'linux' symbolic link.

3. Check that the /usr/src/linux-headers-2.6.7-11-386 really contains what it's supposed to.
3½. If it doesn't, re-extract the headers' tar.gz

4. Make a symbolic link called 'linux' in /usr/src pointing to /usr/src/linux-headers-2.6.7-11-386

---

### Post by krimson on 2007-03-14
that worked like a charm...  just making a symbolic link to linux-headers-2.x.x  did the trick..
thanks!

---

