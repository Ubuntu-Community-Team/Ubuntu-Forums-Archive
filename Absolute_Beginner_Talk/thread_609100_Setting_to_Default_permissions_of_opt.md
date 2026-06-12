---
title: "Setting to Default permissions of /opt"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by zafer34 on 2007-11-10
Hi all, i am new on ubuntu, i have installed xampp on opt, then in it i have installed Joomla, but when i want to install joomla the permissions of folders in joomla all unwrittable so i couldnt install it. I have searched over internet to change the permissions of a folder and sub folders in it. I do like that but now i can not access phpmyadmin becouse of permission. it says the permission should not be world writabe. Then i tried the command to give all permissions to root on /opt. Now i can not access any of the folders and sub folders. I am confused now what to do, i want to rollback to the default permission values, What should i do.

Thank you from now for your help...

---

### Post by pmorton on 2007-11-10
> **zafer34 said:**
> , i want to rollback to the default permission values, What should i do.

Thank you from now for your help...


sudo chmod -R 755 /opt

---

