---
title: "newuser- problem with windows shares"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by karcherb on 2007-04-24
I need some help here. I am new to ubuntu and want to use my ubuntu server (7.04)
to hold files that are accessable to other windows machines. i Tried modifing the smb.conf file 
and restarted samba ( no errors). Now I can see the server on my windows network machines , but cannot login. I get a prompt for user and password but it won't let me in.
I changed the following:
workgroup name ( to match windows)
added path to fles
force user name and force group name

I know I'm missing something . Help ?

---

### Post by oscarwilde on 2007-04-25
May seem like a silly question but have you enabled sharing in ubuntu? This might make a differance.

---

### Post by pebo on 2007-04-25
Sounds like you need to set smbpasswd:```
sudo  smbpasswd -a [your username on the client]
```Set the password. Then you can log in on the client machine.

---

### Post by karcherb on 2007-04-25
Thank You, Thank You, Thank You.
Works Great. I'm transfering my files from my windows 2003 server and shutting it down today !

---

