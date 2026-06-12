---
title: "Permission for shared data folder [Resolved]"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-09
Hello,

I'm newbie Ubuntu user. As  I discovered, there's only one folder by default, where I have permission to edit files: /home/username this folder also includes folder /home/username/desktop, where I also have root permissions, but nowhere else. 

I don't need them mostly but there's one folder including it's branch foders where I keep all my shaded data (I have dual boot) and I want there also to have all these permissions by default. When I right-click on this folder>properties>permissions following appear: Owner: root Group: Root, You are not the owner, so you can't change these permissions.

How can I do that?

---

### Post by darkrose on 2007-04-09
The best option would be to give yourself ownership of the directory it's subdirectories and contents.
Which can be done easily from the command line.
Open a Terminal/Konsole
To give yourself ownership type:
sudo chown -R yourusername /path/to/directory
then enter your password

sudo is to perform a function as root.
chown is to change ownership of the directory.
-R applies the change to all directories and files in that directory.
yourusername is well, your user name, says who you want the new owner to be.
/path/to/directory is whatever directory you want the changes to apply to.

HTH

---

### Post by O-pos on 2007-04-09
Cool! You're an angel! :)

---

### Post by darkrose on 2007-04-09
You're welcome. :)

---

