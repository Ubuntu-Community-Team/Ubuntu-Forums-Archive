---
title: "Installing dual boot over current linux version"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by obzone on 2006-02-13
I am new to ubuntu and am trying to overwrite my current version of Mandrake. but it quickly gets stuck

Can ubuntu be loaded as a dual boot system?

I have booted using the install disk but when it gets to setting the partitions the help page says it won't overwrite a current linux system.
So I tried to reformat the linux partitions as ext2 and ext3 and swap but when I tell it to finish the partitioning it goes away and comes back with:
'No root file system'  so how do I define a root system at this stage? I can't find the option in the partition type list

In the process it has corrupted my mandrake system - not a problem but where do I go from here

---

### Post by lha on 2006-02-13
Instead of manual partitioning, you can tell the installer to erase everything on your disk and create new partitions. This is the easiest solution.

If you want to manually edit partition table, you have to set mount points for your partitions. That 'No root file system' sounds like you forgot to tell installer how it should use those partitions.

---

