---
title: "Create a user and their permissions"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Sig_ZA on 2007-07-28
I see that when you create a new user by default they can view the contents of any folder even those in the file system or another user's /home folder.

1) Is there a way to set up ubuntu so that when you create a new user (through system/administration/users) that by default they can not view the contents of any folder other than their own home folder?

2) Is there an easy way to change the permissions of existing users so that they can only view, change, edit, add to their own folders and have to access to other home folders or file system folders?

Thanks

---

### Post by xopher_mc on 2007-07-28
You need to change the permissions of the files rather than the user's permissions. Each file has root, user, and others permisions. You need to take away others permissions. 

here's how to make home folders unreadable to others. 

sudo chmod o-rwx /home/yourusername/

---

