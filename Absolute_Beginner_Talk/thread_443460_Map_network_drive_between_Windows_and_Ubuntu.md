---
title: "Map network drive between Windows and Ubuntu"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by Linux_n00b on 2007-05-14
I have a folder shared on my Windows XP computer.  How would I be able to connect to that folder and share information back and forth between my Ubuntu system and the Windows XP PC?  Thanks!

---

### Post by echo $USER on 2007-05-14
You have to mount it to the linux file system.  The easiest is to go to Places > Connect to server > Windows share.  Other way is to mount it manually in the terminal or mount at boot by placing the details into /etc/fstab.  If you want to share folders frim Ubuntu to Windows, you will need Samba...

[http://easylinux.info/wiki/Ubuntu:Feisty#Samba_Server](http://easylinux.info/wiki/Ubuntu:Feisty#Samba_Server)

---

