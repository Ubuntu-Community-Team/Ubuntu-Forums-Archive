---
title: "Won't accept new passwords"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Richard.Hatch on 2007-10-05
When I try to create a new user, ubuntu won't accept the password I type in.  This is not the admin password, but the new password for the new user.   For example, I type in terminal

sudo smbpasswd -a newname
New SMB password: abc5de
Retype new SMB password: abc5de
Failed to modify password entry for user newname

I have a similar failure to accept passwords for new users entered through the Users and Groups window.

Any suggestions?

Dick Hatch

---

### Post by zvacet on 2007-10-05
[https://help.ubuntu.com/community/AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")

---

### Post by BrendanM on 2007-10-05
Are you sure the user account you're logged in with is part of "sudoers"? That is, do you have the correct permissions to change passwords?

---

