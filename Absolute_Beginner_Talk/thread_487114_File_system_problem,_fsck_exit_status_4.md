---
title: "File system problem, fsck exit status 4"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by clinto on 2007-06-28
Besides Windows installation giving me a headache, I've got some kind of problem with my file system. I thought it was just something buggy with Kubuntu, but I've installed Ubuntu Studio and it's telling me the same thing.

As it boots, fsck checks the hard drives and partitions. Well, for some reason, when it checks the partition I use to store stuff in, an ext3 filesystem, it gives me: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. It continues to check the other partitions and then says: fsck died with exit status 4.

Then, it tells me the system check failed, gives me the location of the log and tells me to repair the file system manually.

Then it tries opening a maintenance shell. This follows:
```

bash: no job control in this shell
bash: grouops: command not found
bash: lesspipe: command not found
bash: The: command not found
The program 'apt-get' is currently not installed. You can install it by typing: apt-get install apt
bash: apt-get: command not found
bash: dircolors: command not found
bash: The: command not found

```

If I cancel out of it, it loads Ubuntu and everything seems fine. I'm clueless.

In case someone needs to know what I'm doing with my file systems, I'll list my partition table.

hdb1 | ext3 | /boot
hdb2 | linux-swap
hdb3 | extended
hdb5 | ext3 | storage
hdb6 | ext3 | ubuntu /
hdb7 | ext3 | another distro
hdb8 | ext3 | another distro
hdb4 | ext3 | unalloted space

---

