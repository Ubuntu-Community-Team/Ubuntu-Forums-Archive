---
title: "Xserver fails to start"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by digTro on 2006-07-02
While staring up I get this message:

```
GDM: Xserver not found: /usr/X11R6/bin/X :0 -br -audit 0 -auth
/var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the xserver or correct GDM configuration and restart GDM.
```

I think I have accidentally deleted the /usr/X11R6 folder while trying to delete another software.

I tried 'sudo apt-get install xserver-xorg', but it didn't work.

Is there a way to reinstall xserver?

---

### Post by catlett on 2006-07-02
I don't know the partiticulars but a dist upgrade with aptitude should install it.
I would try this first. 
You should have an ubuntu text login. Login with your username and pasword. Thius will give you a command line. Just enter the commands and press enter.
```
sudo aptitude update 
``````
sudo aptitude dist-upgrade
``` This should resolve it because gdm and the xserver are part of the system and this command upgrades the entire system therefore aptitude will notice gdm missing and install it.
If it doesn't work, post and we'll hunt down the exact package name and then install them manually. But try this first, it is the easiest if it works.

---

### Post by digTro on 2006-07-02
I'm sorry, I should have mentioned this in my earlier post. I'm running Breezy Badger. So if I do a dist upgrade, will it upgrade to Dapper Drake?

---

### Post by tseliot on 2006-07-02
[QUOTE=digTro]I'm sorry, I should have mentioned this in my earlier post. I'm running Breezy Badger. So if I do a dist upgrade, will it upgrade to Dapper Drake?[/QUOTE]
No, it won't

---

### Post by richbarna on 2006-07-02
[QUOTE=digTro]I'm sorry, I should have mentioned this in my earlier post. I'm running Breezy Badger. So if I do a dist upgrade, will it upgrade to Dapper Drake?[/QUOTE]

As tselliot said, it won't because you first have to change your repositories to Dapper.
Talking of which, you could actually do a dist-upgrade or download Dapper as it's the newest release.

---

### Post by digTro on 2006-07-02
[QUOTE=catlett]I don't know the partiticulars but a dist upgrade with aptitude should install it.
I would try this first. 
You should have an ubuntu text login. Login with your username and pasword. Thius will give you a command line. Just enter the commands and press enter.
```
sudo aptitude update 
``````
sudo aptitude dist-upgrade
``` This should resolve it because gdm and the xserver are part of the system and this command upgrades the entire system therefore aptitude will notice gdm missing and install it.
If it doesn't work, post and we'll hunt down the exact package name and then install them manually. But try this first, it is the easiest if it works.[/QUOTE]

The upgrade did the trick. Thanks!!

---

