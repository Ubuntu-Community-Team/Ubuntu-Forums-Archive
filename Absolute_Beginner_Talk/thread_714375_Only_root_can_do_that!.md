---
title: "Only root can do that!"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by akafudge on 2008-03-03
Guys, can someone please point me to a resource that helps me understand mounting and directory structures and permissions.

I have been trying to get my freecom usb drive to work but i get messages such as 'only root can do that' so i  need to learn things such as.

1. What is root
2. Why don't I have access and how do I and, why do I need it. 
3. I get a message saying 'Mount is denied because NTFS is marked to be in use' so how do i resolve it?

Cheers.

P.S. 20 years with dos and windows and a week with Ubuntu so take pity on me :confused:](*,)

---

### Post by glennric on 2008-03-03
Root is the administrative user in linux.  To get root access for a command type "sudo" before the command, or "gksu" before running a graphical app.

---

### Post by mikewhatever on 2008-03-03
Permissions --> [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)
chmod --> [http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

### Post by Vitamin-Carrot on 2008-03-03
Root is the admin account for your OS.

under system add your name to the group root in the user and Groups manager.

I cant remember the third one

---

### Post by glennric on 2008-03-03
To answer your 3rd point, it looks like the drive you are trying to mount is already mounted.  Post the output of
```
sudo fdisk -l
```

---

