---
title: "Need the following command..."
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by SilverShadow on 2008-03-28
Hi,
Is there a command or a few commands that can do the following easily:

1. Change the ownership of all the directories and files and subdirectories and files inside those directories etc. inside directory X to user:user
2. Change the permissions for all the files in directory X and it's subdirectories to write- and readable for owner, readable for everyone else.
3. Change the permissions for all the subdirectories in directory X and it's subdirectories to create and delete files for owner, access files for everyone else.
4. Change the ownership of all the directories and files and subdirectories and files inside those directories etc. inside directory X back to root:root

This would be far too much work to do within the Gnome GUI!

---

### Post by Hospadar on 2008-03-28
chown and chmod are the commands you want.  they both have command line switches for recursive behaivor.  do a "man chmod" or "man chown" or look em up on the googletron

---

### Post by Cypher on 2008-03-28
> **SilverShadow said:**
> Hi,
Is there a command or a few commands that can do the following easily:

1. Change the ownership of all the directories and files and subdirectories and files inside those directories etc. inside directory X to user:user

chown -R user.user <direcotry X>
> 
2. Change the permissions for all the files in directory X and it's subdirectories to write- and readable for owner, readable for everyone else.

chmod -R 755 <directory X>
> 
3. Change the permissions for all the subdirectories in directory X and it's subdirectories to create and delete files for owner, access files for everyone else.

chmod -R 755 <directory X>
> 
4. Change the ownership of all the directories and files and subdirectories and files inside those directories etc. inside directory X back to root:root

sudo chown -R root.root <directory X>

---

### Post by lswest on 2008-03-28
well, I'll give you a quick explanation, say you have a folder called "stuff" on your desktop and it's being owned by a user called "tester" but you want to change the ownership to user "test" of group "test2" instead of group "tester2" the command could be ```
sudo chown -R test:test2 ~/Desktop/stuff/
``` where the "-R" is important, as it means recursive, which applies the change to all subfolders and all subfiles.  If you want to change the permissions of a file to "others - read and write" you can do ```
sudo chmod -R o+rw ~/Desktop/stuff
```  hope that cleared it up a bit.

---

