---
title: "[SOLVED] Windows file sharing - incorrect username/password"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by dualityim on 2007-12-02
I am trying to share my home folder using Shared Folders through Windows Networks (SMB). When I am browsing for this computer using my Windows computer, I can see both the workgroup I entered and the name of this computer, but when I try to navigate inside this computer, I am prompted for a username and password. I tried using the user name for this account with the password for this account. I also tried using this computer name\this user name, as well as the workgroup name\this user name. But none of them worked. What is the correct user name format and password combination for accessing Shared Folders on a Windows computer?

---

### Post by Dr Small on 2007-12-02
Try:
```
smbpasswd -a *username*
```
Might have to use sudo, I forget.

---

### Post by dualityim on 2007-12-02
I had no idea Smb administers user names and passwords separately. What you suggested worked beautifully, thanks very much.

---

### Post by Dr Small on 2007-12-02
You're welcome. Please mark this thread as Solved, from Thread Tools :)
Thanks!

Dr Small

---

