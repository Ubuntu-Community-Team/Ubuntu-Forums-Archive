---
title: "Changing file permissions"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Runningflame570 on 2007-11-18
I've been downloading some new games from the repository such as Gem Drop X and I want to be able to use custom icons for them (especially as many don't have their own menu item by default).

The problem is that the /usr/share/icons folder belongs to root and no matter what I try I can't seem to change the permissions on it through sudo or a root shell. I'm probably doing something wrong though. Now I could always log-on as root and change the permissions that way but I think it would save me time in the long run if I learn how to do this.

Can anyone shed some light on the matter?

Heres some different things I tried:

chown [group] /usr/share/icons
chmod a+rw /usr/share/icons
chgrp [group] /usr/share/icons

None of which seem to do anything. All of them were tried with both sudo and a root CLI.

---

### Post by ddrichardson on 2007-11-18
Em, you cannot change the permissions on a folder owned by root unless you are, well root - or at least sudo.

---

### Post by Beaucephus on 2007-11-18
Use sudo to do whatever you need to do in those directories.

Changing ownership/permissions of system folders is never necessary and generally a bad idea.  

For example if your copying files 
```
sudo cp filename /new/directory/filename
```

Also read up on command line usage.  Its really easy to hose your machine if you dont know what your doing.  I recommend_ Running Linux_ published by Oreilly.  I   can almost guarantee it's in your library.

---

### Post by Runningflame570 on 2007-11-18
I've attempted to change them with both sudo and a root shell and its not seeming to work thats the problem.

As for the issue of changing permissions on system folders I don't really think the icons folder would represent a security risk.

---

### Post by Beaucephus on 2007-11-18
Describe what you mean by *change them*.   Nevermind the security risk, your attacking this problem from the wrong angle, thats all.  

If you want to use an image editor you can make copies for editing and then move them back when you have what you want.

```
sudo cp /usr/share/icons/ /home/username/whatever/ 
```
Then apply proper security
```
chmod 666 /home/username/whatever/* 
```
Then you can edit the files.  When you have one you like you can just use another **sudo cp** command to move the file to /usr/share/icons/

In general it is better to use sudo to temporarily give you access rather than change permissions of things.  This becomes more important on multiuser systems, but prevents damage everywhere.

---

