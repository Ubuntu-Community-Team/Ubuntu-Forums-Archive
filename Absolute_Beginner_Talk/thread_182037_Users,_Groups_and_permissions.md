---
title: "Users, Groups and permissions"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by repeat on 2006-05-25
I know how to set permissions on a file/folder.

But i wonder if it's possible to give two different groups different permissions to a file or folder.

An example:

'Group1' includes 'User1' and 'User2'
'Group2' includes 'User3' and 'User4'

'Group1' should have permissions to access 'Folder1' to browse folders and read files.

'Group2' should have all permissions to 'Folder1' and it's content.

How can this be solved? In Windows you can give different groups different permissions to files and folders. Have I missed something. Does it works otherwise in Unix/Linux?

---

### Post by ComplexNumber on 2006-05-25
[quote=repeat]I know how to set permissions on a file/folder.

But i wonder if it's possible to give two different groups different permissions to a file or folder.

An example:

'Group1' includes 'User1' and 'User2'
'Group2' includes 'User3' and 'User4'

'Group1' should have permissions to access 'Folder1' to browse folders and read files.

'Group2' should have all permissions to 'Folder1' and it's content.

How can this be solved? In Windows you can give different groups different permissions to files and folders. Have I missed something. Does it works otherwise in Unix/Linux?[/quote] just go to the user management program (i don't know what it is in ubuntu) and set it there. any individual user can be part of as many groups as required, and any group can encompass however many users.
permissions in windows are rather limited in comparison to *nix.

---

### Post by repeat on 2006-05-25
I'll check that out. I have both Debian and Ubuntu with Gnome.

But I really want to learn how to do this in a console since I don't have any graphical interface on my server box.

---

### Post by halfvolle melk on 2006-05-25
Then check out the man pages for chown and chmod
```
man chown
man chmod
```
What you want to do should be something like this
```
sudo chown :Group2 /folder
sudo chmod +r :Group1 /folder
```
I'm not exactly sure if the above is correct though.

---

### Post by steve.horsley on 2006-05-25
In addition to using **chown** or **chgrp** to change ownerships etc. the file that lists group ownerships is **/etc/group**. man group.

---

### Post by mlind on 2006-05-25
then there's
```

adduser user group

```

which add's user to the desired group. *deluser*  is for removing.

---

