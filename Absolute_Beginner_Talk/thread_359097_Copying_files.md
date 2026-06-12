---
title: "Copying files"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Sabrage on 2007-02-11
Hi. I have some files on the desktop and I want to copy these to another user on my PC. But when I try to cut and paste it says not allowed because I'm not the owner, even though my user has adm. privileges.....:confused:

---

### Post by taurus on 2007-02-11
Not until you use the sudo command.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by shareMenaPeace on 2007-02-11
Hi first of you should use the user which you got on install.

IF you want ADMIN Privileges we use these commands for this which trigger the admin password and let you run as admin.

```
su
sudo
gksduo
```
are these commands

so to copy the files you could either use a terminal 
```

sudo cp /home/Sabrage/Desktop/someFile.iso /home/Xenia/IncomingIsoFiles/
```

or you can use the browser (nautilus) with admin privileges this would go like this

hit ALT + F2
into the popup type
```

gksudo nautilus
```
But be very carefull with these admin rights you can change ervything even by a mistake.

---

### Post by Sabrage on 2007-02-11
Thanks taurus and shareMenaPeace,

The nautilus cmd was exactly was I was looking for. This is perfect. Now I can choose if I want to use the cmd line or the Graphical UI. Thanks so much!

---

