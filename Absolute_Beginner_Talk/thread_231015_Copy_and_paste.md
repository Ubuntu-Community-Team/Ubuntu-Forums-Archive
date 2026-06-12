---
title: "Copy and paste???"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Hawkowl on 2006-08-06
I'm new to linux, ans after tossing options around for my new webserver, decided to go with Ubuntu.
I have installed it with a gnome desktop.
I have it setup up with my windows network and things are going ok.
My trouble is that I began tranferring files from my old webserver across the network to this one.
The files would not copy directly to the /var/www folder. It would say. "permission denied".
I copied them to the desktop of the Ubuntu server and then tried to copy and paste them into the /var/www folder, but it doesn't give me the option. (paste remains greyed out...)
So my question is... how do I go about transferring files into the /var/www folder?
Please explain slowly as I'm a complete newb.
And could you please help by remembering i have gnome installed.

PS I have chosen to SHARE both folders "var" and "www", does this help?

Thanks in advance all :)

---

### Post by batholith on 2006-08-06
I don't know what your /var/www/ folder is (as I don't have one), but it sounds like you need to be logged in as "root" to have write access.

It's as simple as going to a terminal and typing:

$sudo nautilus

type in your password, and it will open up a file manager and you can cut and paste till your heart is content.  

*WARNING*, linux is set up with these safety features (such as the root login) to keep people from wasting their system by mucking around with files, and making it safer from outside attacks.  I'm not sure what kind of files you're moving, but if it is something that will require constant "write" access, I'd try putting your files somewhere else...

---

### Post by catlett on 2006-08-06
The terminal can make your life easy. mv is the command for mv, mv -r is move recursively. So if you had a folder wanttomove and it had alot of files and folders in it, you would just have to mv -r and it would move verything in it's same order.
Let's assume you have folder widget in your old server and you want it in /var/www (I don't know the path to your old servere so I'll make it up)
```
sudo mv -r /oldserver/var/www/widget /var/www
```You enter sudo for root priveleges, mv -r is move recursively, /oldserver/.. is the path of the folder and /var/www is where you want it on the system.
For just a file, use mvg. 
```
sudo mv /oldserver/var/www/document /var/www
```
The mv command will move the file/folder will be moved and will be erased from the original location.
If you want to keep the original then use cp. cp is the command for copy. It works the same way except it keeps the original.
```
sudo cp /home/pictures/picture1 /media/backup
```

---

### Post by aysiu on 2006-08-06
I'd recommend ```
gksudo nautilus
``` instead: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Linux4HumanBeings on 2006-08-06
or if you need acces to root-directory , go in the terminal and type in "sudo -i"

---

