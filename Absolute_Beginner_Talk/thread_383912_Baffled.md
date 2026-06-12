---
title: "Baffled"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by fyrefly on 2007-03-13
Completely baffled. I've gone through the forums, tried different suggestions related to the errors I'm getting, but none seem to be solving the issue.

When I went to boot my computer today, kde didn't load, instead I had the prompt to login in the console. 

startkde failed, so I logged in with startx into gnome - I could only access it in recovery or sudo startx. If I try with my user ID, I get the error:

Server is already active for display. 
If this server is no longer running, remove /tmp/.X0-lock and start again

I removed /tmp/.X0-lock

then get the error when I try to log in again:

xauth: error in locking authority file /home/myuserid/.Xauthority

Also tried:

sudo dpkg-reconfigure -phigh xserver-xorg

Same errors, then
sudo rm -f /tmp/.X0-lock
sudo Xorg -configure
shutdown -r now

Thanks in advance for any suggestions on how I can get the login screen back - and KDE.

---

### Post by Gerard Barberi on 2007-03-13
Check if the .Xauthority file is owned by you and is read/write (600).

---

### Post by fyrefly on 2007-03-13
*[Its owned by root, but I wasn't sure if it was safe to change. Should it be set at 600 for my user ID?]*

Strike that, I changed it and I can log in as my user. But I still don't have the login gui and kde fails to start. I can log into gnome, but would really like to get things working again. :(

---

### Post by fyrefly on 2007-03-15
I figured "no harm" and upgraded to Feisty. Worse case scenario, I would need to reinstall Ubuntu.

The upgrade went perfect, I lost nothing, and everything is working again. 

Happy me :)

---

