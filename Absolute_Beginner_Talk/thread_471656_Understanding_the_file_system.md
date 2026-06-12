---
title: "Understanding the file system"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Brendan Hart on 2007-06-12
I really dont understand the file system, i want everything on a seperate partition, so if i **** up linux, i only have to redo linux rather then loose files.
I just dont know how everything works on it.

any one care to tell me

---

### Post by Princey on 2007-06-12
> **Brendan Hart said:**
> I really dont understand the file system, i want everything on a seperate partition, so if i **** up linux, i only have to redo linux rather then loose files.
I just dont know how everything works on it.

any one care to tell me

You mean directory structure right? File structure refers to file sytems like ext2, ext3 and so on. What you're looking for is this: [http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by choox2 on 2007-06-12
This is a good idea, I always make a partition on my disk for /home and /root. This way if I do something goofy like rm –rf something I needed I can just reinstall the base system. FreeBSD does this by default. Sometimes it’s a problem with adding partitions to a running system, at least it was the last time I tried. But all you have to do is create a partition for let’s say /home. Then just assign that partition the mount point /home. Problem solved. I recomend Google for specifics.

---

### Post by silkstone on 2007-06-12
Take a look at....

[https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html#nautilus-directories-file-systems](https://help.ubuntu.com/7.04/user-guide/C/gosnautilus-8.html#nautilus-directories-file-systems)

That explains the structure of the system files.

In your home folder, if you open the file browser and select View > Show hidden files you'll see lots of directories/folders which start with a dot. The are your configuration files, and the home folder also contains by default all your documents etc. You can choose to have your home folder on another drive or partition, but TBH that doesn't matter too much as long as you back it up occasionally.

---

### Post by choox2 on 2007-06-12
Also sound advie, just do a 
```
man tar
```

And follow those directions and tar up your /home directory and put that on a cd. A more simple solution indeed.

---

### Post by Brendan Hart on 2007-06-12
um, i installed linux on my windows  xp drive so i could dual boot, but soon i want to get rid of it, how do i do that? because when i boot xp, it doesnt come up with the files i put into my xp partition(i got a windows xp partition and a mydocuments partition)

---

### Post by Princey on 2007-06-12
> **Brendan Hart said:**
> um, i installed linux on my windows  xp drive so i could dual boot, but soon i want to get rid of it, how do i do that? because when i boot xp, it doesnt come up with the files i put into my xp partition(i got a windows xp partition and a mydocuments partition)

What exactly do you mean? Unless you created a partition, my documents is a folder under Windows XP. More so, Windows XP uses the NTFS file system while Ubuntu uses ext3 I think by default. These aren't compatible without 3rd party tools. It's like mixing oil and water. So, in simplicity, what do you want to do? Getting rid of XP is as simple as deleting the partition although I'd vote for a clean install letting the Ubuntu installer get rid of the Windows Partition to avoid grub errors upon booting.

---

