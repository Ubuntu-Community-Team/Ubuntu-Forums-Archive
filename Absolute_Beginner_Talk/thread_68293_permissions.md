---
title: "permissions???"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-09-22
How do i set my primary login to be able to browse another users folder? i thought on unix, you simply added the users you want to be able to access a folder, to the other users group.
I cannot read or write it, it simply says you dont have permission. But i have added my normal username to the group for that account, and all the group permissions are ticked?!?

---

### Post by kassetra on 2005-09-22
[QUOTE=dgrafix]How do i set my primary login to be able to browse another users folder? i thought on unix, you simply added the users you want to be able to access a folder, to the other users group.
I cannot read or write it, it simply says you dont have permission. But i have added my normal username to the group for that account, and all the group permissions are ticked?!?[/QUOTE]

Have you logged out of your account after you added those permissions?  Sometimes you have to log out and log back in (not reboot, just log out.)

---

### Post by dgrafix on 2005-09-22
yes tried that. Im now trying to delete my additional users but the folders are still there. rmdir from root simply says folder not empty

tell me theres a way of removing a folder from the conole without havin to delete each file!!

I really dont understand the permissions sytem here. When i add a user, it creates a group. i click on the group and add my primry account name into the list. I log off, log on again and cannot read or write to that users folder in home.  The help on this is terrible, and explains nothing on what putting users in groups does, or wether it creates a group folder somewhere, that anyone in said group has access to.

I tried the wiki but no real help there either,

---

### Post by UbuWu on 2005-09-22
[QUOTE=dgrafix]yes tried that. Im now trying to delete my additional users but the folders are still there. rmdir from root simply says folder not empty

tell me theres a way of removing a folder from the conole without havin to delete each file!!
[/QUOTE]

'rm -r' will recursively delete files and folders

---

