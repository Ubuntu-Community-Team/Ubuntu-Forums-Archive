---
title: "Installed Apache with Synaptic, no conf file?"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by flipz on 2005-11-08
Hi everyone,
I have installed Apache2 many times on windows systems, but I am new to linux. I first set it up manually on Ubuntu (5.10 breezy badger) and had it working completely fine, but I was having all sorts of trouble with getting mysql to work, so I completely reformatted and used Synaptic to install everything (php5, apache2, and mysql).

It's up and running, but now I don't know how to edit things! The httpd.conf file which is how you normally control everything in apache, is a blank file except for a message about only being there for backwards compatability. So how do I edit it? Did it move to a new file? Can I replace it with my old httpd.conf file and then it will read from it? When I set it up myself yesterday (before the format) I used the newest version from the website, and it was still controlled by the httpd.conf file. FYI, some things I am trying to change are logging details, directory listing, virtualhosting, etc. Not just packages or anything because I did notice the folders for that.

As a side note, I was just looking at the php.ini file that was installed with php5, and normally it has an entire list of disabled extensions (they are commented out) and you can go through and enable them. However, the php.ini that was created through synaptic doesn't have that. So how do I do things like enable GD2?

Thanks for any and all help!  :)

-flipz

---

### Post by lreyes6 on 2005-11-08
with the conf file i belive that the name was changed to apache2.conf  and it's located in /etc/apache2 try with that one...

and with the GD you have to install php5-gd and the configurations it's done by sinaptics (or in the command line do a sudo apt-get install php5-gd and that's all)

---

### Post by lreyes6 on 2005-11-08
[QUOTE=lreyes6]with the conf file i belive that the name was changed to apache2.conf  and it's located in /etc/apache2 try with that one...

and with the GD you have to install php5-gd and the configurations it's done by sinaptics (or in the command line do a sudo apt-get install php5-gd and that's all)[/QUOTE]

i forgot something... you have to restart the apache after the installation (sudo /etc/init.d/apache2 restart)

---

### Post by flipz on 2005-11-08
[QUOTE=lreyes6]i forgot something... you have to restart the apache after the installation (sudo /etc/init.d/apache2 restart)[/QUOTE]

Thanks lreyes! You helped me with 2 things, not just GD but with the freaking command to start and stop apache! lol. I saw that it was in services, but I didn't know the command. 

Well make that 3, because you were right, the apache2.conf file does control what I needed it to.  :)  I saw it before, and looked at it, but because it was missing all the extensions that I was looking for, I just assumed it was something different.

You're an ubuntu :KS ! lol. 

-flipz :D

---

### Post by oskude on 2005-11-08
[QUOTE=flipz]Thanks lreyes! You helped me with 2 things, not just GD but with the freaking command to start and stop apache! lol. I saw that it was in services, but I didn't know the command[/QUOTE]
just for the record
most (if not all) scripts in /etc/init.d/ directory take commands: start, stop, restart, reload (reload means reloading config files, but sometimes you need restart even if you "just" edited the config files)

---

