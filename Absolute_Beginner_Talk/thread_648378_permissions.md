---
title: "permissions"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by u_kapaley256 on 2007-12-23
HI.I am a newbie to linux though i have acquired some bookish knowledge.I have this problem that the filesystems as they were already mounted had their owner as root and thus to perform simple tasks such s burning a dvd i have to execute as superuser which was not recommended by the program itself(and rightly so).I tried mounting the filesystems in my home directory but to no avail.What i want to know is that is there some way to do what i want?If not then what is the way to work?I cant keep up with "permission denied" for tasks such as burning a dvd,extacting a tar etc.Any help would be appreciated.......

---

### Post by dward526 on 2007-12-23
try the following command on the directories/files you wish to change permissions

```
 sudo chmod 777 *thefileordirecory* 
```

This changes all permissions to all users, and you should not have denial problems anymore.

---

### Post by vanadium on 2007-12-23
The behaviour you describe is not standard anyway, and would not occur normally after a default install. Did you change something to your account? Did you create a new account using the "adduser" command instead of the graphical interface? In the latter case, you would indeed have to instate (as root) all permissions manually (membership to various groups such as audio or fuse, for example).

---

### Post by u_kapaley256 on 2007-12-25
Hi guys.I worked a bit on the problem but didnt work.Actually i am having my exams so i would try later on.I just came on to say thanks to u guys.I appreciate and would require more of ur help.

---

### Post by meindian523 on 2007-12-25
Instead you could go to System>>Administration>>Users and Groups and look at the permissions you have by selecting Properties of your username,then the Privileges tab will tell you what privileges you have....enable what you want.Also,for the drives not being mounted and read/write access not being allowed to them...you can in Terminal(Applications>>Accessories>>Terminal)

```
sudo gedit /etc/fstab
```

and

type ```
user
``` in the options like default for the partitions(drives) you want to enable mounting,reading and writing by users for......

---

