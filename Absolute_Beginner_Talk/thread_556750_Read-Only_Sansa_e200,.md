---
title: "Read-Only Sansa e200,"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by moocow1452 on 2007-09-21
Hello, people. 

I am trying to get some new music on my e200 player, but when I try to remove old songs and put new ones on, the player says it is a read-only disk that I can't add or delete files to or from. Please Help?

---

### Post by xrdguy on 2007-09-21
Make sure. u have ntfs writer istalled on ubuntu.  if u r using fiesty then use this command in terminal

sudo apt-get install ntfs-config

then go to configuration tab and make sure both internal and external disks are enabled for read and write. u might need to reboot computer. 

second reason could be u dont have root permission. use sudo to have read/write permission on disk.

---

