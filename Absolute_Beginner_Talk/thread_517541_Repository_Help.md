---
title: "Repository Help"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by PhenixRising on 2007-08-04
This is probably an easy problem to fix but I don't really understand Ubuntu yet.  I've run apt-get update and I get the same problems.  I've checked software sources and I do not have any duplicate lists.  I've even looked over the sources list in terminal and I did not see any duplicates.  Let me know if any of you can help me out.

Thanks in advance

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by AlexenderReez on 2007-08-04
> **PhenixRising said:**
> This is probably an easy problem to fix but I don't really understand Ubuntu yet.  I've run apt-get update and I get the same problems.  I've checked software sources and I do not have any duplicate lists.  I've even looked over the sources list in terminal and I did not see any duplicates.  Let me know if any of you can help me out.

Thanks in advance

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

in terminal -->

> gksudo gedit  gedit /etc/apt/sources.list

find 

> feisty-security/main

you will see you have duplicate sources list....so you need to delete one of it:)

---

### Post by PhenixRising on 2007-08-07
Thanks for the help.  The I didn't see exactly what you wrote but I took an educated guess and was right at least I'm not getting the duplicate message anymore.

---

