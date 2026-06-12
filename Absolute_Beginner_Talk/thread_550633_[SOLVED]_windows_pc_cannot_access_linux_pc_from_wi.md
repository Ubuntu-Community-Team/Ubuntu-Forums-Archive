---
title: "[SOLVED] windows pc cannot access linux pc from windows network"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by kubilaycan on 2007-09-14
i use feisty. bob uses xp. we have a network. i can access his shared folders. no problem there. 

he can see my linux pc on the network places in xp, but when he tries to access any folder it asks for a user name and password..

so whassup?

---

### Post by chuckyp on 2007-09-14
If you want to get ride of the prompting for passwords you need to edit your samba configuration file which I believe is /etc/smb.conf and change the following line
security user
to
security share

---

### Post by kubilaycan on 2007-09-14
i did as u said but it still asks for user name and password...

---

### Post by mjwhitfield on 2007-09-14
you'll need to restart samba.

```
sudo /etc/init.d/samba restart
```

---

### Post by kubilaycan on 2007-09-15
i restarted samba, didnt work. and of course i tried again after rebooting. but still no luck.

am i the only person with this problem??

---

### Post by kubilaycan on 2007-09-16
solved: 

just followed this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29)

tip: look out for the semicolon before "security = share" in smb.conf. you have to remove it.

---

### Post by MiKom on 2007-09-16
Can someone tell me how this 'user' security mode works? It looks a bit mysterious because none of the users passwords is accepted, not even the root.

---

### Post by kubilaycan on 2007-09-16
i think u need to add a user id to samba or something. apparently the username asked from a windows pc has nothing to do with your personal login info.

thats why you type in all combinations and none of them work... cuz u need a set one up. kinda unnecessarily complicated... even beaurocratic.

---

