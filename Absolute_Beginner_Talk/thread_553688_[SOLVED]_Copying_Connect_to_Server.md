---
title: "[SOLVED] Copying Connect to Server"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Ginger The Cat on 2007-09-18
I'm not sure of the correct terminology but I have a load of shortcuts on my desktop to ftp servers that I created with the "Places, Connect to Server command".

I am in the process of moving to Gutsy on another partition and want to copy them from their current Desktop to the new Gutsy Gibbon Desktop. I know I could create them again manually but is there any way to copy them all preferably including the associated ftp login passwords.

I am on Dapper.

Cheers

Mike

---

### Post by hyper_ch on 2007-09-18
what ftp program are you using? Normally you'd have in /home/USER config files for your ftp program... it may be hidden (starting with a ".")... but if you copy the config files of your ftp program to the gutsy partition and also the shortcuts created and install the ftp program you should be set.

You could even go further, if you want to operate both OS at the same time and symlink on config folder to the other partition. so you will have only one real set of logins stored but both OS can make use of it.

---

### Post by Ginger The Cat on 2007-09-18
Hi,

I do use an ftp program for anything complicated (gFTP) but in the main I just double click on the desktop icons created by using "Places, Connect to Server"

Right clicking on the desktop icons "Copy" is greyed out.
All I see is Open, Browse Folder, Stretch Icon, Create Archive, Unmount Volums and Properties.

I just thought. Do I need to do some sort of sudo trickery to ungrey the copy option?

Mike

---

### Post by Ginger The Cat on 2007-09-19
Solved, Thanks to [http://ubuntuforums.org/showthread.php?t=83217](http://ubuntuforums.org/showthread.php?t=83217)

Apparently the connection information is stored at ~/.gconf/desktop/gnome/connected_servers/<number>/%gconf.xml

where <number> in my case goes from 1 to 19 with some gaps.

I just had to copy all these <number> folders from my old dapper to the same place in my new gutsy. Then log out and login again. 

Mike

---

