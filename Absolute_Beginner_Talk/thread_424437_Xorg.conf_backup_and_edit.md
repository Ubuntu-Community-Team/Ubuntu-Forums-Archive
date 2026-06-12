---
title: "Xorg.conf backup and edit"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by adampyre on 2007-04-26
Hi,

I made a simple "script" so I have a launcher that automatically backups my xorg.conf and opens it up for editing.... I had to do this because I ran straight to editing the xorg and forgot to back it up first.

you'll want to make a subfolder in X11 called xorgbackup.

you may also want to make a folder in your home directory for this script and others that you might make down the road. I just called mine scripts for this example.

First, make a new text file. Text edit it and place this inside:

sudo cp /etc/X11/xorg.conf /etc/X11/xorgbackup/xorg.bak && sudo gedit /etc/X11/xorg.conf

now save it. I named mine xorg.conf-backup_and_edit

place that file in the scripts folder.

Now make a launcher. There's probably several ways to do this in Gnome but the way I did it is right click the panel I want the launcher on, click "add to panel", click "custom application launcher".

I made "type" application in terminal

name xorg.conf backup and edit

command is where the script is located followed by a ./xorg.conf-backup_and_edit (the name of the script file and a ./ to run it.) so in here for me i put: 
/home/adam/scripts/./xorg.conf-backup_and_edit

a comment as you wish it to be

now close it, place it as you wish on your panel, or dock if you wish. Choose your favorite icon. Clicking on it at this point should automatically backup your current xorg.conf file to a file name xorg.bak in the xorgbackup folder you created. then it will open a graphical text editor so you may edit xorg.conf. since you need su to edit it, you will have to put in your password. You could probably edit the script to automatically enter the password for you, at a security risk. I wouldn't do this unless you like to liv on the edge.... feel free to change gedit in the script to your favorite command line based editor (vi, nano)etc..

I know this is simple for most of you Linux gurus but I'm new to Linux/Unix and this is cool!

Thanks!

- Adam

---

### Post by finer recliner on 2007-04-26
try expanding on it. have it back up your home directory and any other essential files you might want (fstab, sources.list...etc)

then create an alias for it and put it in .bashrc, so you can call it from the command line.

good start though. glad to see you trying to customize your box and write your own stuff :)

---

### Post by adampyre on 2007-04-26
anyone else have any cool scripts/batches they run?

---

