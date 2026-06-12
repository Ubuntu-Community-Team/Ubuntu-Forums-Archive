---
title: "File System Error"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by gramsyn on 2007-06-08
Suddenly, when I was trying to start the system, it was stuck and the following message appeared: File system with errors. It requested the root password to perform maintenance. Then, the following message appeared: 

"The program apt-get is currently not installed. You can install it by typing: apt-get install apt"

The prompt was at the dir: root@user-desktop:~#

I type what I was said by nothing happens. Shoud I change dir and then type this line? If yes in what dir? Or could I fix the problem throug the live CD?

---

### Post by Cypher on 2007-06-08
Ignore the 'apt-get' messages, that has nothing to do with the file-system errors. Look for things like "/dev/hda1" or "/dev/sda1" and similar to see the partition that is not CLEAN, but rather has issues. When you figure out which partition is haivng the issue at the command prompt type:
```

/sbin/e2fsck -y <partition>

```
where <partition> is what you were able to figure out from the messages.

---

