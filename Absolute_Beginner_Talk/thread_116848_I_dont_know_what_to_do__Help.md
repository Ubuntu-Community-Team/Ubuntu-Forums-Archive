---
title: "I dont know what to do  Help"
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by gerardo on 2006-01-13
I need to change some permissions on my file system folders, to put a dictionary on open office i used to do so sudo chown -R gerardo:gerardo /usr, and then i cant do anything else in the terminal when i type sudo i get: sudo: must be setuid root and in administration user and groups i get the following error:
 Child terminated with 1 statusFailed to run users-admin as user root:
 Child terminated with 1 status
What did i do wrong, how can i fix it and how to install a dictionary in open office.
Thanks

---

### Post by d1337 on 2006-01-13
Are you in the terminal as a user that has admin priviledges?  You say "used to", was that on this machine or another.  It looks to me as if you are trying to sudo from a username that hasn't any sudo privs.  Have you made any changes recently in System-->Administration-->Users & Groups that may have brought this on?  For grins, try dropping to a terminal with alt-F1 (or 2-6) and logging in from there.
For the second part, do you have the myspell-en-gb and myspell-en-us packages installed?

d1337

---

### Post by steve.horsley on 2006-01-13
I think you need to re-install. Next time, don't go changing ownership of the whole ***ing operating system.

Edit:
Without the re-install, you can't be sure your ownerships (on which the computers security lie) will ever be right again. Most but not necessarily all files and folders in /usr should belong to root.

To put files into /usr, use **sudo** to gain the necessary root privilege when copying the files in. Use **sudo nautilus** if you feel you must do GUI file management. Do **not** change the whole directory tree just so you can do that change as a normal used. That is definitely taking the mountain to Mohammed.

---

### Post by d1337 on 2006-01-14
As far as I know, everything in /usr is typically root:root.  I would try again to drop to a terminal...try logging as su by doing the following
```
sudo su
```
then you may want to attempt to
```
chown -R root:root /usr
```
and see if this will get you back to where you need to be (but may cause a few other permission issues later...likely not major ones though).  The fix may be so simple as insuring that you are indeed part of the admin group.  If you are able to access a command line (as sudo or root), cat the file /etc/group as follows
```
cat /etc/group | grep admin
```
you'll likely see lpadmin followed by admin which is really what is important here.  Should be something like
```
admin:x:106:d1337
```
of course the 106 may vary value wise and d1337 shoud be gerardo instead.

Hope this helps some,
d1337

---

### Post by BLTicklemonster on 2006-09-05
I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.

---

