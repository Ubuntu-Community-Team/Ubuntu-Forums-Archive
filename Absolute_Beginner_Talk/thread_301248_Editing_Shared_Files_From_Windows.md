---
title: "Editing Shared Files From Windows"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Chewy22 on 2006-11-16
Hi everyone,

Just a quick question. I've poked around in Samba's documentation, but its sorta confusing for me.  Anyway, heres the situation. So far I've managed to get my Ubuntubox to work fine over a network. My main aim was to get a folder shared so I can access the files in that folder from a WinXPbox over the network. So yeah, it's all working, but here's my problem - I want to be able to CHANGE the files in that folder from my WinXPbox, for example, delete files, write files, copy files from XPbox to that shared folder.  At the moment I can only view files.  Here's the code for the following folder in smb.conf:

```
[MyFiles]
path = /home/me/Desktop
valid users = myusername
available = yes
browseable = yes
public = no
writable = yes
```

What command do I add so I can copy files across and delete files? So I need to add:

```
admin users = myusername2
```?

Thanks for your help guys! I must say its harder to work than Win where you can just right click and share files, but this is way more satsfying and quite fun!:mrgreen: 

Regards
Chewy

---

### Post by Joe_CoT on 2006-11-16
See my explanation in [this thread](http://ubuntuforums.org/showthread.php?t=290653).

---

### Post by Chewy22 on 2006-11-17
GREAT! Thanks! Works a dream!

---

