---
title: "enemy territory (and other apps) don't output any sound"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by feest on 2006-08-18
enemy territory (and other apps) don't output any sound, how can i solve this...

---

### Post by rowanparker on 2006-08-19
Edit: Bad link.

---

### Post by OffHand on 2006-08-19
[QUOTE=skirkpatrick]
October 20th, 2005, 02:51 AM
jeffreyvergara.NET: the problem is that you need to be root or sudo to mess with the proc files. Here's an easier way and you don't have to remember to run the commands everytime you want to play:


1) Open a command-line console. Obtain super-user access by either using "su" to change your access or using "sudo" in front of each command. I'll be using "sudo" here.

2) Execute the "runlevel" command. This will tell you what access-level your system is running at. Ubuntu uses runlevel 2 and I believe Fedora Core and Redhat use runlevel 3. I'll be using 2 here.

3) Change to the /etc/init.d directory. Create and edit a file called GameSound. Put the following lines in it for ET:


#!/bin/bash
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm1c/oss

You can add or substitue q3.x86 for et.x86 for Quake 3.

4) Change the permissions on GameSound with the following:

sudo chmod 755 /etc/init.d/GameSound


5) Change to the /etc/rc2.d directory

6) Create a symbolic link to have GameSound automatically run on startup:


sudo ln -s /etc/init.d/GameSound ./S99GameSound


Reboot and things should be taken care of. If you find another game that's having a problem, add it to the GameSound file.



Also, I've got the latest version and have no problems seeing servers in the Server Browser.[/QUOTE]

Try this

---

### Post by ColdDeath on 2006-08-19
Odd, I had the exact same problem on the exact same day as you.

That HOWTO worked fine and fixed my sound! Thanks to subsonic for making me aware of the solution, thanks to skirkpatrick for writing it,

---

### Post by rowanparker on 2006-08-19
Good job you got it working. (Although I didn't help :D)

---

### Post by feest on 2006-08-25
well that help file didn't help my sound output but it did fixed the problem that my cd rom was not recognized, further it now gives an error at starting hp & linux printing system [fail] (the last time i had this i couldn't stat x window (which does work) so it could have been worse...

---

### Post by feest on 2006-08-25
owyeah, while loggin into gnome (i usally use kde) i get some errors and my printer failsss :S

---

