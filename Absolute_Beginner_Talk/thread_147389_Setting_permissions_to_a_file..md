---
title: "Setting permissions to a file."
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by LinuxLove on 2006-03-20
I'm installing Cedega 5.1 on my computer, and I've unpackaged the files as root. Now all that is left is for me to run the file, but I can't do this because the file isn't set as executable. Furthermore I cannot change it to executable due to the fact I'm not root.

Now, I know how to gain access as root in terminal, but not outside. How can I go about to change this file to executable so that I'm able to run it?

---

### Post by sublime on 2006-03-20
sudo nautilus

then just navigate to the file

---

### Post by colo on 2006-03-20
Open a terminal, type in
```
sudo su -
```
to elevate your privileges to those of the super-user-account. Change to the directory the file(s) you want to make executeable reside in, and issue
```
chmod a+x YOURFILENAMESGOHERE
```
there. You should be set by then.

---

