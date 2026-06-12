---
title: "Ubunut not starting after an update for nvidia ??"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Najmudin on 2007-06-12
There was an update for Ubuntu  , after finishing the update it asked me for restarting the system , when i restart the system i got this screen :
[IMG]http://img153.imageshack.us/img153/5947/1206071547gp9.jpg[/IMG]

After entering my user name & password i got this screen :
[IMG]http://img502.imageshack.us/img502/7453/1206071548sn8.jpg[/IMG]
I cant do anything to start Ubuntu again , so what should be written in this case to make it run again.

---

### Post by dstew on 2007-06-12
I think Ubuntu is running fine, but your Xserver is not. Try at the command prompt```
sudo dpkg-reconfigure xserver-xorg
```to re-configure your X server, the software that provides your graphical user interface. When you are done reconfiguring, enter **startx** on the command line and see if she goes.

---

### Post by Seisen on 2007-06-12
Try typing in startx and see what happens.

---

### Post by muximus on 2007-06-12
your ubuntu is running fine.. and the nvidia installation should edit the xorg.conf file properly by itself. as seisen suggested, try startx, xinit or gdm on that prompt <called command prompt>

---

### Post by Najand on 2007-06-12
If Startx doesn't work, type:
```

sudo nano /etc/X11/xorg.conf

```
Then Push Enter.
Then Enter your password and press enter again.
Find  "Section "Device"
and change "nvidia" to "nv"
And then Push Ctrl+X => Y
Then reboot using, "sudo reboot"

---

### Post by burt_57 on 2007-06-12
I have been having same problem.
Now I have formatted the second drive.
Did a fixmbr.
Now I am in Windows Xp... grrrrrrrrrrrrr.
Going to reinstall.
But first I have use Norton Ghost to back my first hardrive and check if 
it all will work fine.so far so good.
Now closing windows and going back to reinstall Ubuntu /I386 for the 5 th time I think :-k

---

### Post by Crafty Kisses on 2007-06-12
> **Najmudin said:**
> There was an update for Ubuntu  , after finishing the update it asked me for restarting the system , when i restart the system i got this screen :
[IMG]http://img153.imageshack.us/img153/5947/1206071547gp9.jpg[/IMG]

After entering my user name & password i got this screen :
[IMG]http://img502.imageshack.us/img502/7453/1206071548sn8.jpg[/IMG]
I cant do anything to start Ubuntu again , so what should be written in this case to make it run again.

When you attempt to install the drivers again, you should back up your X server file, and then if anything goes wrong in the future you can easily recover it. :p

---

### Post by Najmudin on 2007-06-12
> **Najand said:**
> If Startx doesn't work, type:
```

sudo nano /etc/X11/xorg.conf

```
Then Push Enter.
Then Enter your password and press enter again.
Find  "Section "Device"
and change "nvidia" to "nv"
And then Push Ctrl+X => Y
Then reboot using, "sudo reboot"

Startx was working with me , but i did not understand what to do or change there i tried your instruction to change the "nvidia" to "nv" then rebooting using "sudo reboot" and it worked perfectly with me:D .
When i tried using the "nano"  i just did not know how to find "Section Device" ??? i tried using sreach but there was no result.
Any way thanks allot for you and other guys who tried to help me with the problem , thats what i call real support.;)

---

### Post by Najmudin on 2007-06-12
> **Codename said:**
> When you attempt to install the drivers again, you should back up your X server file, and then if anything goes wrong in the future you can easily recover it. :p

Can you give an instruction or a link on how to backup the X server.

---

### Post by Crafty Kisses on 2007-06-12
> **Najmudin said:**
> Can you give an instruction or a link on how to backup the X server.

Sure, to back up your X server file, go into terminal and type: 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then if anything goes wrong you can recover it by typing:

```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

Hope this helps. :p

---

### Post by Najmudin on 2007-06-12
> **Codename said:**
> Sure, to back up you X server file, go into terminal and type: 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then if anything goes wrong you can recover it by typing:

```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

Hope this helps. :p

Thanks Mate , sure it will help.:)

---

### Post by Najand on 2007-06-12
You may have problems with Beryl, etc. If so try to install the restricted drivers for nvidia.

---

### Post by Crafty Kisses on 2007-06-12
> **Najand said:**
> You may have problems with Beryl, etc. If so try to install the restricted drivers for nvidia.

Yeah you might, but nothing a little configuring can't fix. :p

---

