---
title: "[SOLVED] user denied access"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by boogar on 2007-01-29
I have not activated my admin psswrd yet but one of my users is being denied access. Have I been script attacked? or has other hanky panky taken place ?

---

### Post by taurus on 2007-01-29
One of your users has been denied access to your machine over the net--ssh or ftp?

---

### Post by boogar on 2007-01-29
this is right at the key board, With the other user I visited some antiwar sites with this user I have not. The last site I used was craigslist other than that nothing unusual and I've made no changes to my settings for quite a while.

---

### Post by taurus on 2007-01-29
So you have two accounts on your machine.  You can log in with one but somehow can't with the other!  Is there any error message when you try to log in with the second account?  See if you can log in with the second account from a console--<Ctrl><Alt>F2!  To get back to your GUI login screen, press <Alt>F7.

---

### Post by boogar on 2007-01-29
Yes there is a message: user name OR password are incorrect. I have not changed my password though and caps lock was off, It should have worked.

---

### Post by taurus on 2007-01-29
Can you run sudo with the first account, the one that you are able to log in?  Maybe you can change the password of your second account.  

Log in with the first account and open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo passwd **username**
(where **username** is the log in name of your second account)
```
Now, log out of the first account and see if you can log in with the second account with that new password.

---

### Post by boogar on 2007-01-29
I got:

Sorry, try again.
Password:
 
so it sees the user just doesn't accept the password

---

### Post by taurus on 2007-01-29
Even with the new password that you have changed?  

Log back in as a first user and post the output of this command here.

```
cat /etc/passwd
```

---

### Post by boogar on 2007-01-29
OK what am I looking for? The #'s at the bottom are to cover user names

root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List
Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats
Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:101:101::/nonexistent:/bin/false
syslog:x:102:102::/home/syslog:/bin/false
klog:x:103:103::/home/klog:/bin/false
cupsys:x:100:106::/home/cupsys:/bin/false
messagebus:x:104:107::/var/run/dbus:/bin/false
haldaemon:x:108:108:Hardware abstraction layer,,,:/var/run/hal:/bin/false
hplip:x:105:7:HPLIP system user,,,:/var/run/hplip:/bin/false
gdm:x:106:111:Gnome Display Manager:/var/lib/gdm:/bin/false
####:x:1000:1000:####,,,:/home/mine:/bin/bash
beagleindex:x:107:65534::/var/cache/beagle:/bin/false
mysql:x:109:114:MySQL Server,,,:/var/lib/mysql:/bin/false
######:x:1001:1001:mcsailor,,,:/home/######:/bin/bash

---

