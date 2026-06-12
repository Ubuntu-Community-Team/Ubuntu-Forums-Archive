---
title: "Permissions question"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2007-11-13
Hi, a while ago I placed a lot of files on my iPod in order to move them from one computer to another and am now not able to delete them from the iPod once I no longer need them on the iPod. I can move and copy (not cut)  them to other hard drives and files, but I am told I do not have the proper permissions to delete them. Any ideas (also maybe an explanation as to why this happens)? Thanks so much for your time.

---

### Post by arpanaut on 2007-11-13
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by celsdogg on 2007-11-13
also check to see who the owner of the files are. the fs may not regard you as the owner and/or you may not have write permissions on the file. in a terminal, type in ls -l to get ownership and permission information.

---

### Post by kevindubrow on 2007-11-14
Thank you both for your replies, the second reply is what I ended up following and it worked great! Thanks for your help!

---

