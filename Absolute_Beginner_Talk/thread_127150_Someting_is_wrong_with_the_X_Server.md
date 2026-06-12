---
title: "Someting is wrong with the X Server"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by z3r0-c0d3r on 2006-02-08
When I start up Ubuntu I get the message that says that X server couldn't be loaded and I need to configure it but then before I can do anything the CDI interface comes and tells me to enter the Ubuntu login and password.

This is after I installed DRI (tried atleast)

Can someone help me with this??Please

---

### Post by christhemonkey on 2006-02-08
Login, then,
Type
```
sudo dpkg-reconfigure xserver-xorg
```

Then select appropriate answers to all the questions.
When this is finished, type:
```
sudo /etc/init.d/gdm restart
```
(replace gdm with kdm if using kubuntu)

---

### Post by z3r0-c0d3r on 2006-02-16
I tried that but it doesnt work!!

These are the instructions i followed to try to install it
> This is how you install Xorg and modules.tar.bz2: 

Download Xorg.bz2 and modules.tar.bz2. 

Make a backup of /usr/X11R6/lib/modules and usr/X11R6/bin/Xorg (if present) and move them out of the way. 

Uncompress Xorg.bz2, copy it to /usr/X11R6/bin and set permissions. 

Uncompress Xorg-modules.tar.bz2 in /usr/X11R6/lib. 

Make a symbolic link from /etc/X11/X to /usr/X11R6/bin/Xorg if it's not there yet or points somewhere else. 

If needed copy XF86Config-4 to xorg.conf and change the keyboard driver from "keyboard" to "kbd". 

The following sequence of commands should work in bash: 
```

wget http://dri.freedesktop.org/snapshots/extras/Xorg.bz2
wget http://dri.freedesktop.org/snapshots/extras/modules.tar.bz2
 
mv -f /usr/X11R6/bin/Xorg /usr/X11R6/bin/Xorg.backup
bzip2 -d Xorg.bz2
cp Xorg /usr/X11R6/bin
chmod 4755 /usr/X11R6/bin/Xorg
 
mv /usr/X11R6/lib/modules /usr/X11R6/lib/modules.backup
tar -C /usr/X11R6/lib -xjf modules.tar.bz2
 
cd /etc/X11
rm X
ln -s /usr/X11R6/bin/Xorg X
if [ -f XF86Config-4 ]; then cp XF86Config-4 xorg.conf; fi
<edit xorg.conf>

```


Can someone tell me how to reverse this??Please

---

