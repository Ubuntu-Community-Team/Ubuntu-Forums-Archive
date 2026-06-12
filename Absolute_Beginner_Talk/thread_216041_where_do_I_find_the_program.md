---
title: "where do I find the program?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by suver.17 on 2006-07-14
I installed iripdb, an iriver mp3 player program.  I installed it through the synaptic package manager, but I can not find the program so I can run it.  I have looked through my applications menu, as well as the debian menu within the applications menu.  How do I go about finding/running the program?  

Thanks
Jared

---

### Post by uzi09 on 2006-07-14
have you tried to refresh the gnome-panel yet??
if not, try this and look through the menu's again:
```
killall gnome-panel
```

if that still doesn't work, you may have to run it through the terminal. just try to call the name of the program.

---

### Post by suver.17 on 2006-07-14
i still dont see it in the menus, and when I call the name on terminal i get this:

@ubuntu:~$ iripdb
error: no path provided
Usage: iripdb [-vhesuc] path_to_ihp

---

### Post by scxtt on 2006-07-14
that program is for updating the database on an iRiver iHP-1xx (do you have one?) ... and to use it you have to type:
[indent]iripdb /dev/sda1[/indent]replacing /dev/sda1 w/ the **actual** path to your USB iRiver device ... it's probably not gonna show up in the menu because it's not a normal gnome app or that 'feature' wasn't coded into the .deb package ...

---

### Post by PhilOSparta on 2006-07-14
Another way to find any file on your system is to first update the system database by using the terminal command   ***sudo slocate -u***
It will request your password if you haven't used sudo in awhile.

Wait until the prompt comes back (about a minute or so) because the whole database is updated.

Next enter locate and your file name.
Example:  You are trying to find some program aaa.xyz
Enter the command   ***locate aaa.xyz***   
If it is in your system, it will be listed with its full path.

Actually, xyz would list all the files that have xyz in them.

Neat!

---

