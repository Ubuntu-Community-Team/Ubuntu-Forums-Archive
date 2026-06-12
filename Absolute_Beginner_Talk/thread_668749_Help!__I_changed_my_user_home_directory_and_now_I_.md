---
title: "Help!  I changed my user home directory and now I can't log in"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by The Realms of Gold on 2008-01-15
Hey everybody, I'm new to Ubuntu and I've run up against this popular problem.

I'm running Ubuntu 7.10 and Gnome as a single user on a machine with a single hard drive, which, like All Gaul, is divided into three parts.  I have two NTFS partitions, one for Windows XP and one for all my personal files, and one EXT3 partition for Linux.

In the user preferences, I changed my home directory from home/username to media/sda1, which is the location of the personal-file partition.  Of course I got the "User's $HOME/.dmrc file is being ignored" error and its accompanying less-than-ten-seconds session problem, and got dumped right back at the login screen.

The failsafe session didn't work (I didn't try failsafe with terminal), though recovery mode did.  I executed startx, and got Gnome, but I was logged in as root, of course.  So when I went back to the user prefs to change the directory back, I got root's preferences and not my own, which was no help.

After the "ignored" error when trying to log in normally, if I click the checkbox to show the report details, I get the following error:

```
Refusing to initialize GTK+.

/etc/gdm/Xsession:  Beginning session setup...

Could not set mode 0700 on private per-user gnome configuration directory '?media/sda1/.gnome2_private/':  Operation not permitted.
```

I need to reset the home directory to /home/username, without creating new users or messing with groups or anything like that.  As far as I know this isn't a permissions error and it's a single-user system.  If anybody knows what to do I'd greatly appreciate it!

P.S.  somebody please tell me you got the "All Gaul" reference :-)

---

### Post by yabbadabbadont on 2008-01-15
First off, only native linux filesystems can be used for a user's home directory as they are the only ones that support the required permissions.  ;)

To fix your issue, boot into recovery mode and use the "usermod" command to change the home directory of your normal user back to what it was before.
```
usermod --home /home/username username
```

Edit: No, I didn't get the "All Gaul" reference...

---

### Post by The Realms of Gold on 2008-01-15
It worked!  Thanks!  I figured it had something to do with the nature of the NTFS partition.  Is there any way to make the home directory point or redirect to the root level of my personal-files NTFS partition?  I have barely any space on the Linux partition and I can't just copy all my files onto it.

By the way, the "All Gaul" reference is to Julius Caesar's *Commentaries on the Gallic Wars*, which begins:

> All Gaul is divided into three parts, one of which the Belgae inhabit, the Aquitani another, those who in their own language are called Celts, in ours Gauls, the third.  All these differ from each other in language, customs and laws.

---

### Post by cheahk on 2008-01-15
You don't need to move it.  Just use a symbolic link:

For example, in your home directory. /home/user
```
ln -s /media/sda1/   ntfsspace
```

This means that you can just change into that /home/user/ntfsspace "directory" to access all your stuff.  (rename ntfsspace to whatever you want).

-K

---

