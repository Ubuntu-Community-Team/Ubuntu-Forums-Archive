---
title: "Installing Lotus Symplhony on Ubuntu"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by koidenouvo on 2007-10-01
Hi,

I lack hard drive space to install and test this huge beta software.

When it comes to the installation wizard, I want to set up this install location:

**/media/sda7/Symphony_Beta/Symphony_Beta**

but i get this message : 

**"Cannot install to /media/sda7/Symphony_Beta/Symphony_Beta. The path needs to be readable by all users."**

I would like to understand here what is the path. Is it about my hd partition or my folder/directory? I tried to change the permission of Symphony_Beta to make it readable by all user but I can't, here is the output of _ls -l _:

**drwxrwx--- 2 root plugdev 4096 2007-10-01 14:38 Symphony_Beta**

If my partition is concerned, below is my _fstab_ for the partition:
[B]
# /dev/sda7
UUID=B884-37C6  /media/sda7     vfat    defaults,utf8,umask=023,gid=46 0       1[/B]

Can you help me out with this and help to understand a little this issue.

Pascal

---

### Post by j.bunce on 2007-10-02
Copy it to your home directory, and run the program from there.

---

### Post by koidenouvo on 2007-10-02
my home directory is on a separate partition with insuffiscient space disk...

---

