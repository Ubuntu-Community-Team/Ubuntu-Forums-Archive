---
title: "am I root?"
date: 2005-09-23
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-09-23
When I log into ubuntu, i use the username that i chose during installation.  Is that user name the same as root?  I am concerned because i have read several statements saying that you should never log in as root.  How would I log in as root?

---

### Post by SilentCacophony on 2005-09-23
Hello. Ubuntu does not set up a root account as such. Instead, it uses **sudo**. Prefix any command that you need to run as root with sudo, and it'll prompt you for your normal password, and run that command as root. For instance, should you want to edit the /etc/fstab file, which requres root access, you'd execute:

sudo nano /etc/fstab

---

### Post by aysiu on 2005-09-23
Read this:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

