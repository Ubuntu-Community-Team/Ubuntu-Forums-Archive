---
title: "hon do i"
date: 2005-08-02
forum: Absolute Beginner Talk
---

### Post by aran384 on 2005-08-02
im wanting to map folder for /var/www to home directionary for the users in /home/<user> 

ive read this guide here

[http://ubuntuguide.org/#mapURLstofoldersoutsidewww](http://ubuntuguide.org/#mapURLstofoldersoutsidewww)

but i dont understand it or how to change it to get what i want... 

can some1 please help???

---

### Post by timmir on 2005-08-02
Depending on what you want there are two ways.
If you want to change all requests to the web server to be served from your home folder then change the /var/www line in the apache config file to your home folder.  If you don't feel like messing with apache configs you can just use a symbolic link instead.

1. open a terminal
2. type 'cd \var'
3. (optional) type 'sudo mv www/* /home/user' (if you want to save the data in /var/www move it to the new folder)
4. type 'sudo rm -rf www' (This will erase the wntire www directory)
5. type 'sudo ln -s /home/user www'  (This will create a symbolic link to the new folder)

---

### Post by aran384 on 2005-08-02
yeah but will this make it so every user i create will its own public_html folder?????

---

