---
title: "General Issues"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by anoncompboy on 2005-12-23
I just installed Ubuntu and I am having a slew of general problems that are stopping me from getting any work done:

1) dont have permissions to change anything - rename, create, or delete folders.

2) wireless card isnt even detected. Found that the right drivers are [madwifi]("http://www.madwifi.net/"), I downloaded it but its just a heap of files

3) can't mount my FAT32 partition that I created to share files between Windows and Linux. I successfully mounted my NTFS partition read-only, and I learned how to mount correctly. But when I try to mount the FAT partition it gives me this text dump about mounting and doesnt do what I asked.

Help would be great.

---

### Post by `GooZ´ on 2005-12-23
1) use the command 'sudo nautilus'
2) try your windows driver with ndisgtk
3) Instructions at [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by anoncompboy on 2005-12-24
Thanks, that solves #1, now I am trying to solve #3, the mounting. I know what to do (im following a great guide) but I have one problem - i created a folder named "Shared Partition". When trying to delete it with "rmdir Shared Partition" it tries to look for a folder called "shared" and a folder called "partition" to delete. I have tried "rmdir Shared_Partition" but it doesnt work that way either. How do I remove a folder with a space character in its name? Cant do it in GUI as it belongs to root.

---

### Post by timfrost on 2005-12-24
Put it in quotes:

```

  sudo rmdir "Shared Partition"

```

---

### Post by kaamos on 2005-12-24
Try ```
sudo rm -rf Shared\ Partition
```
Or just type until "Shared" and press tab. Might also be a good idea to avoid using folders with spaces as a "just in case" rule.

---

