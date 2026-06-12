---
title: "hi - and question about deleting files"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by pscalgary on 2007-09-02
Hi, 

I'm new to this - just installed Ubuntu this w/e, pretty impressed so far, quick install, all hardware automatically recognized and a lot of good software installed rightaway!

However- I do have a "problem". I created two users, both with admin privileges. One works fine but on the other one I am not able to delete or add files to the desktop. Deleting and adding files to the home folder is fine.

Any ideas?
Thanks!
Peter

---

### Post by annda on 2007-09-02
check the permissions. more info is here:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

if you need more assistance, please post again.

---

### Post by mikewhatever on 2007-09-02
What happens when you try deleting a file from the desktop? Do you get any messages, or nothing at all happens and the file remains?

---

### Post by softtower on 2007-09-02
What error message do you get? Whose desktop is that? Do you realize that each user has its own desktop? Assuming you have "mary" and "bob":

Mary's desktop is /home/mary/desktop
Bob's desktop is /home/bob/desktop

Even if both of them are administrators, they (by default) should not have permissions to write to each other's desktops. Administrative status only allows you to change permissions, not to avoid them.

Good luck.

---

### Post by InGunsWeTrust on 2007-09-02
```
sudo chmod -R 777 /home/usernamwithreadwriteproblems/Desktop
```

This will make it so everyone on the computer can read and write to that particular desktop.

---

### Post by bapoumba on 2007-09-02
When logged with your user that does not have admin privileges, what does return:
```
groups
```
(Open a terminal: > Accssries > Terminal, and run the command, then paste the complete output in here).

---

### Post by pscalgary on 2007-09-02
Thanks for the response!

I realize both users have their own desktop, deleting from the one worked  but not from the other one.

Error message was: 
"Cannot move ... to the trash because you do not have permission to change it or it's parent folder"

This worked:
sudo chmod -R 777 /home/usernamwithreadwriteproblems/Desktop

Thanks again!!
Peter

---

### Post by ddrichardson on 2007-09-02
> **InGunsWeTrust said:**
> ```
sudo chmod -R 777 /home/usernamwithreadwriteproblems/Desktop
```This will make it so everyone on the computer can read and write to that particular desktop.

This is true but extremely inadvisable - especially setting the world bit to 7 - giving read/write/execute access to those outside the user and group.

---

