---
title: "Reparing installation - User home drive lost"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by sa125 on 2008-01-15
I installed ubuntu alongside WinXP from scratch, making sure I formatted my HD before installing both. I started installing stuff and somehow messed up my users setting, changing my user home from /home/me/
to /root/ ... Dumb, I know. No I can't log in -- I get an error saying **User's $HOME/.dmrc file is being ignored" -- and not sure how to repair that, since I'm the only user on the system.. File should be owned by user and have 644 permissions.** Any idea how to repair that before I format the drive and re-install?.. Thanks.

---

### Post by Iowan on 2008-01-15
There is a rescue mode in GRUB (when the system first starts up) that lets you go into a single-user (root) mode.  As usual, I'm not at home to get specifics... and my memory "just ain't that good no mo'".

---

### Post by sisco311 on 2008-01-15
> **sa125 said:**
> I installed ubuntu alongside WinXP from scratch, making sure I formatted my HD before installing both. I started installing stuff and somehow messed up my users setting, changing my user home from /home/me/
to /root/ ... Dumb, I know. No I can't log in -- I get an error saying **User's $HOME/.dmrc file is being ignored" -- and not sure how to repair that, since I'm the only user on the system.. File should be owned by user and have 644 permissions.** Any idea how to repair that before I format the drive and re-install?.. Thanks.

boot in recovery mode and type:
```
usermod --home /home/**your-username-here**/ **your-username-here**
```reboot in normal mode

---

### Post by sa125 on 2008-01-15
Thanks, that did it.

---

### Post by hyper_ch on 2008-01-15
> **sa125 said:**
> Thanks, that did it.

Now use your backup files to restore all the altered configuration data ;)

---

