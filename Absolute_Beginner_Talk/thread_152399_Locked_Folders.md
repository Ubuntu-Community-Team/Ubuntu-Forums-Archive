---
title: "Locked Folders"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by poser on 2006-03-29
I have found some instructions on setting up an email server in ubuntu, and thought it would be a fun little project.  So anyway I have to make some changes from the looks of it, to some config files in different programs.  

Anyway the first folder that I have to go in to check certain files etc it locked.   When ever I try to open it in Konqueror it just tells me I don't have permissions, and i can't change directories to it in the command line for the same reason.

I need to know if there is some way I can get into this folder (or others in the future)

thanks

---

### Post by aysiu on 2006-03-29
Read this.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by belikralj on 2006-03-29
If you wish to access the folders from Konkerer (did I spell it right?) you will have to open a terminal and openid by prepending sudo to it like "sudo konkerer" this gives you root permitions (unlimited access) in konkerer but to modify the files you will probably need to type something like "sudo gedit filename" sudo opens the file as root (super user/administrator) gedit is the text editor on my machine you should replace this with your equivelant and filename is the name of the file you wish to modify (filename or directory same thing). Sorry if I made this sound too simplistic it's just quicker to explain everything rather than guess your level of expertise.

Hope this helps    ;)

---

