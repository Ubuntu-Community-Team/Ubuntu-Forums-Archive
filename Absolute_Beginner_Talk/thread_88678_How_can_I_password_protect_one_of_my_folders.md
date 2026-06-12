---
title: "How can I password protect one of my folders?"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-11-10
I need to password protect one of my folders.  Is there a way to do this in Ubuntu?

---

### Post by ssam on 2005-11-10
if you right click on a folder and you to properties, then go to the permissions tab you can decide who can read or write to the folder.

i think by default all your folders give everyone read access.

---

### Post by 23meg on 2005-11-10
[Nautilus locked folders]("http://www.ids.org.au/~jam6/locked-folders/") looks good for this purpose, it's still in development and may not be 100% safe though.

---

### Post by Sutekh on 2005-11-10
If the folder is under your /home/username folder then it is password protected from other users, and can only be viewed in a session where you are logged in.

To protect a folder when you are logged on, follow this section in the Ubuntu guide - [Q: How to open files as root user via right click?]("http://ubuntuguide.org/#browsefilesfoldersasrootnautilus")

Then if you set the permissions of the folder to root, in the way ssam suggested then you will only be able to get into the folder by right-clicking the folder and  choosing 'scripts' then 'open as root' and then enter your password.  

A new broswer window should open that will allow you to access that folder. but only while that window is open.

---

