---
title: "folder and file permissions"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by doughardy on 2007-06-12
just a newb question please guys

Linux ubuntu 2.6.20-15-server 

using  SSH Secure Shell 3.2.9 (Build 283)

the command below is what ive been using to change permission of the bf2 folder to 777 which works fine 

xxxxxxx@ubuntu:~$ sudo chmod 777 /EAGAMES/bf2/mods/bf2

could you help me on the command line on how to change a folder and all its sub folders and file permissions at the same time 
                                          
thankyou

---

### Post by Cypher on 2007-06-12
Just add "-R" to the chmod command and it will apply the same permissions to all files and sub-folders...so
```

sudo chmod -R 777 /EAGAMES/bf2/mods/bf2

```

---

### Post by testube_babies on 2007-06-12
use the -R flag

that is...

sudo chmod -R 777 /path/to/folder

---

### Post by doughardy on 2007-06-12
Thats  Great Guys  Thanks Very Much For You Help  All Sorted

---

