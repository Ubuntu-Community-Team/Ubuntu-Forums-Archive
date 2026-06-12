---
title: "how to use nautilus to browse files in gnome - edgy?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by nadav2605 on 2006-11-30
i just installed apache + php + mysql on my edgy desktop version and i was wondering why i don't have permission to write files in /var/www.
i want to be able to move directories and files, delete files and overwrite files and folders.
i heard i can use nautilus to do it in gnome, how exactly do i do that? should i do it that way?

thanks!

---

### Post by catlett on 2006-11-30
nautilus is the application that opens when you hit on "computer" and "home" on your desktop or when you go to the top panel and enter into Places>Home Folder etc.
You will only have permissions to alter things in your Home folder. To alter folders/files elsewhere you need to be root (a.k.a. need administrative powers) To become root at the command line you preface commands with sudo. To become root using nautilus so you can do things in a gui environment, you need to launch nautilus as root.
To launch as root, open a terminal and entere```
 gksudo nautilus
```Nautilus will open in the root "home" folder. Just browse to the file/foldeer you want to change/delete. Just be careful, you can delete anythimng as root.

---

### Post by CatKiller on 2006-11-30
Some stuff on permissions:

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

