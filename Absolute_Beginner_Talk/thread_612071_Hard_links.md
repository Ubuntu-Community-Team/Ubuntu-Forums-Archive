---
title: "Hard links?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by erqu1 on 2007-11-13
I have run into a situation I am hoping someone can help explain the results I am getting. It is related to the 'ln' command. I am told that you can not create hard links across filesystems. Well I seem to be able to. According to a article I read the "ln /bin/rm del should not work. I believe my problem is with the definition of filesystem. If I am in my home directory and issue the command should I not get an error. Why is this working? Any ideas Please.

---

### Post by vanadium on 2007-11-13
One file system is one partition. You can create hardlinks for data residing on the same partition, (provided the file system supports hard links).

If your /home is on your system partition, then it is normal that you do not get the error: /bin/rm is on the same partition as your home.

---

### Post by erqu1 on 2007-11-13
That makes sense...Could you help explain the partition concept. Is it related to disk drives? If I had" /bin" on a different device then "/home", would it fail then. Is there anyway to experiment with the command if I only have LINUX installed on a single HDD.

---

### Post by CatKiller on 2007-11-13
[http://en.wikipedia.org/wiki/Disk_partition](http://en.wikipedia.org/wiki/Disk_partition)

---

### Post by bodhi.zazen on 2007-11-13
> **erqu1 said:**
> That makes sense...Could you help explain the partition concept. Is it related to disk drives? If I had" /bin" on a different device then "/home", would it fail then. Is there anyway to experiment with the command if I only have LINUX installed on a single HDD.

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

