---
title: "user permission from root"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by prostock3 on 2007-07-18
i'm trying to add permission for my username to the apache2-default folder.  currently, only root has permission to add/ modify the contents.

first, i added my username to a group by (i'm not sure if this is the write way):

usermod -a -G users "username"

Then i logged on as root and used nautilus, 


From there, I go to the apache2-default folder and change the items to:

group==>users
Folder access==> Create and delete files

Then I try creating a file in the apache2-default directoy, but it doesn't work.  I also want other users to be able to access this folder.  That is why I wanted to make it group accessible.


Thanks in advance.

---

### Post by Cappy on 2007-07-18
It's ```
sudo usermod -aG groupnamehere $USER
```

You can change what group controls a folder and all of its contents like so:
```
sudo chown -R $USER:groupnamehere /path/to/wherever/
```

and you can change the folder and all of its containing files to read/write like so (for the group):
```
sudo chmod -R 775 /path/to/wherever/
```

That's what I did to my /var/www so that I can copy stuff over there without using sudo. Makes sharing files easy.

If you chmod -R 777 all users will be able to access and write to the folder regardless of if they are in that group or not.

---

