---
title: "Help!!!!"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by RCKola on 2006-04-30
I don't know what to do! everytime i try to get in to one of my administrator prefs, i type in my root password and the window just closes, nothing opens. I try to do a task thru terminal and enter my root password, and ubuntu still doesn't listen to me! do i have to reinstall or what!

---

### Post by hw-tph on 2006-04-30
Read the [wiki article on sudo](https://wiki.ubuntu.com/RootSudo). The password you should enter is not the root password but your own.

By default there is no root password set; instead administration tasks is done using sudo.


Håkan

---

### Post by RCKola on 2006-04-30
my root and personal password are the same, the problem is that any program that requires a password to open, will not open.

---

### Post by christhemonkey on 2006-04-30
Try running
```
gksudo gnome-window-properties
```
(i think thats on the admin menu!)

and then report any errors it spits out in the terminal.

---

### Post by RCKola on 2006-04-30
just my luck, window properties opened just fine, no errors.

---

### Post by RCKola on 2006-04-30
maybe i should be more specific, it wont onpen user prefs.

---

### Post by xenmax on 2006-04-30
Did you do an expert install? Sounds like that since you have root account enabled (unless you did this yourself). 
If expert install, try this thread (especially codejunkie's posts)
[http://ubuntuforums.org/showthread.php?t=146859]("http://ubuntuforums.org/showthread.php?t=146859")

---

