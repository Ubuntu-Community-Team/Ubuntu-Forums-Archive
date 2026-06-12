---
title: "sudoers file"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by hwe001 on 2006-05-03
what is sudoes file? how can i be added to this file to do some sudo things?

---

### Post by aysiu on 2006-05-03
You're not already in the *sudoers* file? If not, someone else will have to add you in. Is someone else using the first account created during installation?

---

### Post by catlett on 2006-05-03
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
This is a good place to start. You have sudo powers. The install takes care of it. It is a way of invoking root priveleges without logging off/on from user to root. You need it to change anything not in your home folder. It is used like this```
 sudo apt-get install Galeon
```
Then it asks for your password. Put in your regular user password you log on with. Then it will run the command. This example is my invoking root to install the Galeon web browser from the apt repositories. Sudo/superuserdo, apt-get:/get the package from apt repositories, install/install it, Galeon/the name of the package I want to get and install.

Didn't see previous post. Good question. Do you NOT have sudo ability when you use SUDO before a command?

---

