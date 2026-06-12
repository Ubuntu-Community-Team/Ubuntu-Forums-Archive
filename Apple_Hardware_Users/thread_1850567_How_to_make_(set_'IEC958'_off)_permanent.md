---
title: "How to make (set 'IEC958' off) permanent?"
date: 2011-09-26
forum: Apple Hardware Users
---

### Post by Asgard20032 on 2011-09-26
I really start to freakout, having a pointer laser on my macbook pro...
If i enter the command on the terminal, it work... but how to make it permanent?
I made a bash script. THE BASH SCRIPT WORK! But i can't make the computer load it on startup.

I tried to do the same thing i did in my bash script in /etc/rc.local
Also tried /etc/init.d/local
Also tried putting the bash in /etc/init.d/Myscript.sh and making a link to it from a rc#.d (tried every rc#.d rc1, rc2... evem rc0.d and rcS.d)

And yes, i did chmod +x

How the hell do we do start up script in ubuntu... each time, i tried to execute the script to be sure it work, but when i restart... the laser is back until i MANUALLY execute the script.

The only way i can make the script load on start up, is by using the 'Start Up Application' utility... but its not what i want, i want the red laser to be disabled BEFORE i log in, not after the login screen...

Mackbook pro 5,5

Latest ubuntu version

---

