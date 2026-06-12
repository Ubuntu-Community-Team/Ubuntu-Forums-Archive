---
title: "Changing Groups in Linux?"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by djseto on 2007-04-18
I am new to Linux still and I am still getting up to speed on the whole permissions structure. Whenever I copy or create music files on my machine, I am doing it under my username: djseto. When I try to play the music back in MythTV via MythMusic, it doesnt work because the files were created by djseto (me) and not under MythTV. When I go to mange users and groups in the GUI, I only see myself and Root. I dont see MythTV, but I also followed an install guide, so I dont quite know how the user MythTV was setup. All I want to be able to do is add music as needed and not have to chmod or chown everytime. Is that possible? If so, how do I do it?

Thanks

---

### Post by jordanmthomas on 2007-04-18
```
usermod -aG *newgroupname* *username*
```
will add a user to a group.

Is this what you were looking for?

---

### Post by BoneKracker on 2007-04-18
There is probably a button to "show all users" or something.  It seems to be only showing you the users who can actually log in.

By the way, when you run an application, it has access to whatever files you have access to (unless it has been specifically set to use a different user id when it runs).  So your problem with MythTV probably has a different cause.

---

### Post by djseto on 2007-04-18
I guess what I want is to give the user "mythtv" read/write/execute access to anything the user"djseto" has. I figured if they were in the same group, they could without me having to chmod files everytime i add them. The application MythTV is started by the user "MythTV", but aside from starting MythTV, the user djseto is who I log in as for anything I do on the machine.

---

### Post by jordanmthomas on 2007-04-18
```
sudo usermod -aG djseto mythtv
```
should probably work.  I am not familiar with how Ubuntu sets up its groups initially, but it seemed like last time I used it my user had his own group and it was the primary group.

---

### Post by djseto on 2007-04-18
ok. ill try this out. thanks

---

