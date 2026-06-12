---
title: "how to get to  a network drive through cli"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by dynacrylic on 2007-01-08
I need to copy a some files from my Kubuntu 6.10 box to my windows box. How do I navigate to a samba network drive from konsole? I'm trying to save some files before I reformat...

---

### Post by troymcdavis on 2007-02-05
I find the easiest way to do something like this is to use SMB4K. It's fairly straight forward. Once you get it up and running, you would just```
cp /directory/the/file/is/in/file.ext /home/user/smb4k/folder/
```
Let me know if you have any questions. Best of luck to you!

---

