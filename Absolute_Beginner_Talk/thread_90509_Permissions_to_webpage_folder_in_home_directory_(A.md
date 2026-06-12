---
title: "Permissions to webpage folder in home directory (Apache) (Solved)"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by mr_crimp on 2005-11-15
Hi, 
I just got Apache + PHP4 succesfully installed. The server is just for local tests of webpages on my laptop, so it is not used as a "real" webserver. I have changed the DocumentRoot to my webpage folder in my home directory(/home/me/webpage). 

My only problem is that Apache does not have persmissions to acces the folders and files in the webpage folder. I have tried to change the persimissions of the content in the folder to 777 and then it's working, but that can't be a good solution? What shall I do? Is there a solution where I don't have to change the permissions of every file or folder I make in the webpage folder?

Edit: I copied my webpage folder from windows and the permission of all the files is by default 700.

---

### Post by heimo on 2005-11-15
Add yourself to www-data group (Apache runs as www-data user), change all the files and directories of your webpages to www-data:www-data
```
chown -R www-data:www-data /path/to/files
```

Change all the directories to be group writable and "SGID" (chmod g+ws /directory). This way, all the new files and directories will have group set to www-data. Gererally you want files to be something like 664 (-rw-rw-r--) and directories to be 775 (drwxrwsr-x) and owned by group www-data

---

### Post by adwait on 2005-11-15
Change the username of of apache to your own in /etc/apache2/apache.conf.
Find the line
[quote]user <whatever>
group <whatever>[/code]

Change the settings to your own username and group. Alternatively, you can change the ownership of the directory to that mention the config file, but then you'll have to use sudo each time to edit the files.

---

### Post by mr_crimp on 2005-11-15
Thank to both of you. I only tried Heimos solution because it just worked. But once again thanks for both yours solutions.

---

### Post by Goochi on 2005-12-18
I just tried the second because the first didn't do it for me :p
Also thanks both either way.

---

