---
title: "cd New Volume (no such file or directory)!!"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by maher_79 on 2007-06-10
Hi all,

I'm trying to cd to this folder or hard drive (New Volume) but i keep getting "No such file or directory"
I thought it might be because of the space so i tried to change the name on it but i can't do that either.

```
root@maher-ubuntu:/media# ls
cdrom  cdrom0  cdrom1  floppy  floppy0  New Volume
root@maher-ubuntu:/media# cd New Volume
bash: cd: New: No such file or directory
root@maher-ubuntu:/media# 

```

Please Help :(

---

### Post by Outrunner on 2007-06-10
That would be ```
cd New\ Volume
```

EDIT: Or you can type cd New and press tab to autocomplete

---

### Post by Bohlio on 2007-06-10
```
cd /media/New\ Volume
```

---

### Post by trak87 on 2007-06-10
or use quote characters:

```
cd "New Volume"
```


One of the coolest features at the command line is command-line completion as mentioned by Outrunner above. To try it, do this:

```
cd "New<tab>
```

Press tab once after "New" and it should automatically insert the " Volume" part without having to type it in. Here's a another trick. Let's say you want to look at all the files beginning with b in the /usr/bin directory:

```
ls -l /usr/bin/b<tab><tab>
```

Press tab twice after the letter "b" and it will list a bunch of files (executables in this case) beginning with b.

---

### Post by maher_79 on 2007-06-10
Ok, now - i'm trying to change permissions on "New Volume" to have full access (read, write, delete) - i'm doing the below command and the following results

I appreciate the help guys :)

```
root@maher-ubuntu:/media# chmod 777 New\ Volume
chmod: changing permissions of `New Volume': Read-only file system

```

What is it trying to say by "Read-only file system" - Where is this setup at?!

---

### Post by Outrunner on 2007-06-10
What exactly is New Volume? Is it a NTFS partition? If so, you'll need to use ntfs-3g to write to it. That's all I can tell you since I never needed to access a NTFS partition from Linux.

---

### Post by maher_79 on 2007-06-10
> **Outrunner said:**
> What exactly is New Volume? Is it a NTFS partition? If so, you'll need to use ntfs-3g to write to it. That's all I can tell you since I never needed to access a NTFS partition from Linux.

Yes it is  - i dual boot with Vista and this Hard drive has been in use before i loaded Ubuntu.

What is ntfs-3g?  Sorry new to Ubuntu and would love to dump Windows :D

---

### Post by Outrunner on 2007-06-10
It's a third party(unsupported) application that allows you to write to a NTFS partitions. [Here's]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G") a HOWTO about it.

Good luck.

---

