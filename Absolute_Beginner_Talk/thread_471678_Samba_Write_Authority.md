---
title: "Samba Write Authority"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by R_U_Q_R_U on 2007-06-12
Ok, I am an Ubuntu noob with only a dim clue of what do.

I have set up Samba on my 7.04 machine and added the XP user accounts and password information. I setup the config file with a share under [MyFiles]. Good so far. I can see the shared files on the XP box but that is all. I want to be able to copy files from the XP box to Ubuntu over the network.

I am really confused about "root" and file ownership. How do I give the XP user write authority to the shared folder in Ubuntu?

Also, when I right-click on a file to view properties I see the dialog is all grayed out and the owner is "root." How do I change ownership to a file or group of file.

Thanks.

---

### Post by starcraft.man on 2007-06-12
Ok, I think its just a minor problem with the permissions of the files. You can fix that easy and I have two guides for you to read that should get ya to solve it.

[Psychocats basic permissions]("http://www.psychocats.net/ubuntu/permissions")
[URL="http://www.linuxcommand.org/lts0070.php"]
Linux Command more complete explanation of permissions.[/URL]

I'm sure you'll be able to fix it easily after reading those two :).

---

### Post by R_U_Q_R_U on 2007-06-12
> **starcraft.man said:**
> Ok, I think its just a minor problem with the permissions of the files. You can fix that easy and I have two guides for you to read that should get ya to solve it.

[Psychocats basic permissions]("http://www.psychocats.net/ubuntu/permissions")
[URL="http://www.linuxcommand.org/lts0070.php"]
Linux Command more complete explanation of permissions.[/URL]

I'm sure you'll be able to fix it easily after reading those two :).

THANKS so much. This is exactly what I was looking for!

---

### Post by starcraft.man on 2007-06-12
> **R_U_Q_R_U said:**
> THANKS so much. This is exactly what I was looking for!

Your very welcome. The file permissions system is a bit weird if you been using Windows all this time. It is very powerful though and I think nicely done. Just takes a bit of reading to fully understand and then you can do tonnes of things with it.

Have fun with Ubuntu, and Linux Command is a great place for learning CLI/Scripts.

---

