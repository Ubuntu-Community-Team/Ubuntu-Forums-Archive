---
title: "How to insert php file into the /opt folder"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by mthalis on 2007-09-11
I installed xampp in my machine. It installed /opt/xampp folder. To the excute php file I have to insert php /opt/xampp/htdoc folder but I can't insert files that folder because it is a root dirctory. How can i insert file that location or how can run php.

---

### Post by jw5801 on 2007-09-11
No idea about php, but to move a file to the folder:
```
sudo mv /*folder*/*file* /opt/xampp/htdoc/
```
or if you want to retain a copy in it's original directory:
```
sudo cp /*folder*/*file* /opt/xampp/htdoc/
```
You'll need to replace the italics with the file you want though :p

---

### Post by bvanaerde on 2007-09-13
You'll have to be root to be able to copy files to /opt/lampp/htdocs/
I found that quite annoying...

So I tried this ([COLOR="Red"]DON'T DO THIS[/COLOR]):
> sudo chown -R <my_username> /opt/lampp/htdocs/ 
But for some reason this broke the Xampp config pages (at localhost/xampp/)

So I made a new user group called "web":

System > Administration > Users and Groups
Manage groups
Add group
Group name: web
Members: root & <my_username>

Then, I changed the group permissions:
> sudo chgrp -R web /opt/lampp/htdocs/
sudo chmod -R g+w /opt/lampp/htdocs/

You need to log off & login again to apply changes.
Now you can add & modify the htdocs content.

---

### Post by eduardounder on 2007-09-13
Instead of changing permissions, I use:
> 
sudo nautilus


And if I want to edit it..
> 
sudo gedit


The only problem, is the 15 minutes sudo limit, so sometimes (when editing lots of file) I do a 'sudo su' first.. then just remove the sudo in front the commands.

You can also make shortcuts..
Just use 'gksudo' instead of 'sudo'. (If you are at gnome).

---

### Post by jw5801 on 2007-09-13
You should use gksudo regardless. If you use sudo with a graphical app it can mess up the permissions and owners of files, which can mean that in extreme cases, you can break some fairly important things, note what happened above upon changing the ownership of /opt/lampp/htdocs (although he did that himself :p)

---

### Post by huangweiqiu on 2007-09-13
Hi Bro

it is easy to copy files into system fold,just type : [COLOR="Navy"]sudo nautilus [/COLOR]      on the the terminal ,then you can copy the files into system folder with permission .
----------------------------

[www.linuxine.com](www.linuxine.com) :lolflag:

---

### Post by jw5801 on 2007-09-14
> **huangweiqiu said:**
> Hi Bro

it is easy to copy files into system fold,just type : [COLOR="Navy"]sudo nautilus [/COLOR]      on the the terminal ,then you can copy the files into system folder with permission .
----------------------------

[www.linuxine.com](www.linuxine.com) :lolflag:

If you're opening a graphical application as root ALWAYS use gksudo, not regular sudo! (See my above post)

As for opening nautilus as root... be EXTREMELY careful, I've seen people accidentally delete folders that are mildly necessary and completely trash their system. I wouldn't recommend it anyway, just copy it across from the command line. If you're constantly changing a file in there, then make the file you have in the folder owned by root, a symlink to the file in your home directory. That way you can do whatever you like to the file and not have to worry about copying it back every time.```
sudo ln -s ~/*file* /*root-owned-folder*/*file*
```

---

