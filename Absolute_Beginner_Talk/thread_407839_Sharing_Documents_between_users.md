---
title: "Sharing Documents between users"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2007-04-12
I want to share some of my documents in my home folder with my wife. She has a separate account on the same machine.

I want to make a symlink on her desktop to some of the documents in my /home folder, and give here read/write permissions in only those directories. This way we don't end up with multiple versions of the same documents spread accross 2 different home directories.

How do I set up the permissions to give 1 user wr access to 1 directory?

---

### Post by compmodder26 on 2007-04-12
I would personally create a new group.  Add both accounts to that group, and then change the group ownership of the shared folder to the new group (sudo chgrp newgroup /path/to/shared/folder).  Then change the permissions of the folder to allow group writing (sudo chmod g+w /path/to/shared/folder).

---

### Post by thornomad on 2007-04-12
I'm not sure of specifics, but I believe you can use the chown command to change the group owner of the specific folders to a group that you and your wife share.  So, you may have to create a new group (addgroup) then add your wife and yourself to the group, then change the ownership of the folder to that group ... and then, I don't recall how, there is a way to set the folder to automatically apply the folder's group permissions to the files that are created/saved in that folder.

Wish I knew more details, myself; abstract, I know.  Sorry.

---

### Post by DSn0wMan on 2007-04-12
Thanks compmodder26 creating a separate group was a perfect solution.

Edit: @ thornomad - The change the ownership recursively you can use ```
 chown -R user:group filename
```

---

