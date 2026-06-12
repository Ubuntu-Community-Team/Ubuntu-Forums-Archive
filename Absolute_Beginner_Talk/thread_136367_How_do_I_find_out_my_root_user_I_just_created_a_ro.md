---
title: "How do I find out my root user I just created a root password."
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by YellowHat on 2006-02-25
I need to use easy ubuntu.

---

### Post by procras on 2006-02-25
The root user is called
root

The first `normal` user created in the installation can do all the
sudo root things with their own password
$ sudo fdisk /dev/sdb
Password: 

This user can get a root shell with the command
$ sudo -s

---

