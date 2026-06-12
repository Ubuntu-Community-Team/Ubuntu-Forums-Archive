---
title: "GDM could not write to your authorization fle"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by toontastic on 2007-06-02
After finally getting past the ati problems I am now getting the error:

```
GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case it is not possible to login. Please contact system administrator
```

I noticed that when I finally got the install working it seemed to find another version of Ubuntu which I believe must be a failed version and it seemed to create new partitions but the partitions still came to a total of 23gb so I'm sure that should be more than enough space.

I tried changing sessions using the options down the bottom left to login but it didn't seem to change anything.
Any ideas how I can log in and start using this product that everyone tells me is great but I can't get working :D

---

### Post by toontastic on 2007-06-02
I managed to fix this problem as well. Just in case anyone else has this problem I went in through recovery mode then entered

aptitude clean

df -h

shutdown -r now

and that let me log in. It seems after looking at the disk usage analyser that my home folder is only 732kb and it's using 100%. Any ideas how to increase the size of this ?

---

