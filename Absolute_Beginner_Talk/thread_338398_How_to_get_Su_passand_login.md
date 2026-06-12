---
title: "How to get Su pass/and login?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by dragonmine on 2007-01-14
Hey all im trying to install programs but when the password for su comes up it says authentication failure , i got no idea how to get my su pass so if anyone can help me out with that it would be really appreciated.

---

### Post by zerhacke on 2007-01-14
The root user has no password.  It is disabled.

Instead, use sudo to do things as root.  When it asks for the password, put your own password in

---

### Post by ardchoille42 on 2007-01-14
> **dragonmine said:**
> Hey all im trying to install programs but when the password for su comes up it says authentication failure , i got no idea how to get my su pass so if anyone can help me out with that it would be really appreciated.

The root account is disabled by default in Ubuntu, for security reasons. If you need to run an app for admin tasks, use sudo or gksu. Sudo for command line apps, and gksu for gui apps.

---

### Post by Fahuadai on 2007-01-14
> **dragonmine said:**
> Hey all im trying to install programs but when the password for su comes up it says authentication failure , i got no idea how to get my su pass so if anyone can help me out with that it would be really appreciated.

Hello dragonmine,

If you are using the console, please use the following to install:

sudo apt-get install <package>

To search:

sudo apt-cache search <to search parameter>




Alternatively if you're using the package manager, such as adept or synaptic, when it prompts for the password, as zerhacke said, then enter your normal login password when prompted.

---

### Post by aysiu on 2007-01-14
Read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by dragonmine on 2007-01-14
it dosent say its a package though its just et-linux-2.55.x86.run

---

### Post by Albi on 2007-01-14
> **dragonmine said:**
> it dosent say its a package though its just et-linux-2.55.x86.run

if you need to su, do sudo su and enter your password

---

### Post by Pobega on 2007-01-14
Or, another alternative is *sudo -i* or *sudo -s*.

---

### Post by houstonbofh on 2007-01-14
> **dragonmine said:**
> it dosent say its a package though its just et-linux-2.55.x86.run
Fun game, but not the easiest to start with...  Did you install the binary drivers, and test them?  First, make sure you are in the directory with the file.  Also make sure it is marked executable.
```
sudo ./et-linux-2.55.x86
```
Put in your password.

---

### Post by dragonmine on 2007-01-14
hauston where are the binary drivers
And i dont have permission to put my installs in directors
You don't have the right permissions to create an archive in the destination folder.

---

### Post by houstonbofh on 2007-01-15
> **dragonmine said:**
> hauston where are the binary drivers
And i dont have permission to put my installs in directors
You don't have the right permissions to create an archive in the destination folder.
Hopefully, you are typing your commands with more care to spelling then your posts.  A single typo can make it fail.  If you are getting permissions errors, then you are not running sudo.
Try the howto here...
[http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)

---

### Post by jordanmthomas on 2007-01-15
or he forgot to make the installer executable
maybe??
```
chmod +x et-linux-2.55.x86
sudo ./et-linux-2.55.x86
```

---

