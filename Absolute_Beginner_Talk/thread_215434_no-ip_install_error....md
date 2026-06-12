---
title: "no-ip install error..."
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by Mitsusl on 2006-07-13
Hey guys... when I use the command: 

*sudo apt-get install no-ip*

I get the following error:
[I]
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package no-ip[/I]


I'm stumped on what to do or try next.](*,)  Any help would be appreciated. Thanks.

---

### Post by T700 on 2006-07-13
It's located in the [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe repository.  You have to enable that in your source list and then do a sudo apt-get update.

Paul

---

### Post by Sef on 2006-07-13
Have you added to your repositories?  [Click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by Mitsusl on 2006-07-13
> **Sef said:**
> Have you added to your repositories?  [Click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Thanks a bunch, its now installed and running. Do I need to do anything else so that no-ip will automatically start when the box is rebooted?

---

