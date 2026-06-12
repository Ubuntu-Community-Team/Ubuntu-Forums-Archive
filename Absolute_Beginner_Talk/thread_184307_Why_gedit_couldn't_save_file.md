---
title: "Why gedit couldn't save file?"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by cpthk on 2006-05-29
Why gedit couldn't save file?

Everytime I use gedit to edit some conf file for example httpd.conf. When I pressed save, it will say couldn't save /usr/local...

I already changed the file owner to this account.

---

### Post by Harold P on 2006-05-29
Does it say you don't have the right permissions? It might be that you aren't running it as a super user. Do this:

```
sudo gedit whatevery/your/file/is
```

---

### Post by ComplexNumber on 2006-05-29
[quote=cpthk]Why gedit couldn't save file?

Everytime I use gedit to edit some conf file for example httpd.conf. When I pressed save, it will say couldn't save /usr/local...

I already changed the file owner to this account.[/quote] its exactly as Horald says. there is nothing in /usr directory that an ordinary user should be able to have write permissions to. you should only have write permissions to your own home directory....nothing else. do not change the write permissions of the file - its not recommended at all. its bad practice to change write permissions or ownership in any other than youir home directory. access the file using gksudo gedit, as Harold P says

---

### Post by aysiu on 2006-05-29
Never change file ownership or permissions on a system file. That's a quick way to render your system unusable.

Read this instead:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by denizenx on 2008-03-21
say, how do I save it in gutsy? is there some place that I can enter a password for sudo in the GUI?
the GUI doesn't gel very well with all this user permissions thingy.

---

### Post by Mustard on 2008-03-21
If you really must use the GUI rather than the command line, then try this....

1. Press ALT+F2
2. Enter this command in the input box..
```
gksudo nautilus
```
3. Hit Enter
4. Enter your user password in the password prompt
5. You are now browsing the system as the 'root' user with full permissions, so be very careful what you do.
6. Browse to the file you with to edit and open it in gedit
7 Edit file and save
8. Close the window you opened with root privileges, so you dont accidently change something else

Most of the steps above could be done with one command in the command line..

```
gksudo gedit /whatever/location/your/file/is/at/filename
```

---

### Post by Mustard on 2008-03-21
> **denizenx said:**
> ..the GUI doesn't gel very well with all this user permissions thingy.

The GUI actually does exactly what it is supposed to do.  It restricts access by normal users to the system files or administrative files.

Ubuntu is set up this way for very good reasons.  With Ubuntu, an administrator has complete control of the system.  The account that you log in with is technically not the administrator account, but a normal user account that has been granted access to administration.  The real administration account is the 'root' account.

The administrator has great power and to coin a phrase used recently in a recent popular movie, with great power comes great responsibiity.  Before you execute any administrative power, it is your responsibility to know the ramifications of the execution of that power.

---

### Post by 3rdalbum on 2008-03-21
Install the package "nautilus-gksu". Log out, then log in again. You'll now be able to right-click files and choose "Open as Administrator", which will prompt for a password.

Then you can make whatever edits you want.

Don't change permissions on system files; the permissions are there for Very Good Reasons.

---

