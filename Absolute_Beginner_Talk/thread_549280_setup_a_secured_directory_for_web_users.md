---
title: "setup a secured directory for web users"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by angelochen960 on 2007-09-12
Hi,

I'm using a Ubuntu server with Tomcat to run a web application, I have a folder in the file system that contains images, I'd like to configure it in such a way that user can access a specfic file if he knows the file name, but he can't access anything else, how to set it up? Thanks.
A.C.

---

### Post by macogw on 2007-09-12
That's more of a web development question than general beginner computer stuff.  I'd suggest asking on an appropriate IRC channel (based on the language you're using, or maybe just Apache2)

---

### Post by bigboy_pdb on 2007-09-12
If I remember correctly, Tomcat uses your folder permissions to determine how someone should access a folder.

The read bit in a folder allows someone to read the folder contents. The write bit allows someone to change the contents of a folder. The execute bit allows a person to enter the folder.

You want the world (visitors without privileges on your system) to be able to enter the folder but you don't want them to see it listed. The global permissions on the folder affect whether or not the world can see a directory listing within your folder. Thus, change the directory settings of the folder that you don't want people to see the contents of so that it only has global execute permissions.

For example, if I have a folder called "f2" that is within a folder called "f1" and I want other people to see the contents of f2 but not f1 (meaning they must know that f2 is in f1) then I must change the contents of the folder f1 so that only the global execution bit is enabled.

You can see this by doing the following:
```

#Create f1
sudo mkdir f1

#Create f2 within f1
sudo mkdir f1/f2

# Gives the owner (which is root) permission to read the contents of, change the contents of, and enter f1 (because of the 7)
# Gives the (root) group permission to read the contents of and enter f1 (because of the 5)
# Gives the world permission to only enter f1 (because of the 1)
sudo chmod 751 f1

# This cannot be done because only root can list the contents of f1
ls f1

# This can be done because root can see the contents of f1 (because root both owns it and has permissions to do anything within his/her system)
sudo ls -ld f1

# You can do both of the following because the world has permission to see the contents of and enter f2 
ls f1/f2
cd f1/f2

```

If you need more information regarding this, you can do a search in google for "Linux directory permissions".

---

