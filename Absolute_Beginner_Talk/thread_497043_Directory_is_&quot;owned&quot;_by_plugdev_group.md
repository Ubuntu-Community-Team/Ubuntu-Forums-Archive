---
title: "Directory is &quot;owned&quot; by plugdev group?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Tsu Dho Nimh on 2007-07-09
I can't delete a directory from the trash because it has suddenly become owned by root and the group "plugdev".  I do not have a group of that name on the system.

What is this group and how do I get it to turn loose of my directory so I can empty the trash?

---

### Post by wormser on 2007-07-09
This should work.

Applications> Accessories> Terminal

```
gksudo nautilus ~/.Trash/
```

Then enter your password and delete the file.  Gksudo is like sudo but for graphical apps.  Be careful with it because you can really mess up your system by deleting system files.

---

### Post by Tsu Dho Nimh on 2007-07-09
OK ... first I get this, 
"GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension"


And when Nautilus shows me the ./Trash, it's empty.

But it's NOT empty.

---

### Post by Nekiruhs on 2007-07-09
The above poster forgot that when you open a root app at ~ it opens at roots home hone yours. Just type ```
gksudo nautilus /home/YourUsername/.Trash
```

---

### Post by punx45 on 2007-07-09
what is the directory?   plugdev is the group for removable devices...  are you sure you need to be deleting the directory?

---

### Post by Tsu Dho Nimh on 2007-07-09
It insists my trash is empty ... but when I open the trashcan on the toolbvar, it's not empty and the directory and files owned by root and that non-existent group are still there.

It's the ./trash directory.  with a directory of data that has become redundant.  It was created in Windows, as were other directories I have deleted.

I have no clue how plugdev became the group that cpontrols the file with root.

---

### Post by punx45 on 2007-07-09
hmm.. so you cant delete the trash files through the GUI right?
use the terminal.
```
cd ~/.Trash
sudo rm -rfi *
```
that should do the trick.

and as always, rm is powerful and dangerous, especially with sudo power, so do be carefu.   sudo be careful :lolflag:

---

### Post by Tsu Dho Nimh on 2007-07-09
me@fossil:~$ cd ~/.Trash
[email]me@fossil:~/.Tras[/email]h$ sudo rm -rfi *
rm: cannot lstat `*': No such file or directory
[email]me@fossil:~/.Tras[/email]h$ 

There is nothing in there to be deleted, but the desktop trash says it has contents.

---

### Post by punx45 on 2007-07-09
hmm.. well that must be a problem with gnome then..   can't help ya there.

---

### Post by Tsu Dho Nimh on 2007-07-09
Roomie came home and found the problem ... 

Somehow Linux created a directory called .Trash-me (me is my user name) and assigned it to root and plugdev  and its contents (Data1 and it's subdirectories) were showing up in the trashbin.  Because I can't log on a root in Ubuntu, I have no clue what happened, but here's what he was doing:

me@fossil:~$ sudo bash
Password:
root@fossil:~# pwd
/home/me
root@fossil:~# cd /.Trash
bash: cd: /.Trash: No such file or directory
root@fossil:~# ls a
ls: a: No such file or directory

**root@fossil:~/.Trash# find /media/hdd1 -iname trash**  (looking for anything resembling "trash"
[email]root@fossil:~/.Tras[/email]h# ls -la /media/hdd1
total 7108
(skip a long list)
**drwxrwx---  3 root plugdev   49152 2007-07-09 17:09 .Trash-me** (FOUND IT!)

[email]root@fossil:~/.Tras[/email]h# ls -la /media/hdd1/.Trash-me/
total 80
drwxrwx---  3 root plugdev 49152 2007-07-09 17:09 .
drwxrwx--- 11 root plugdev 16384 2007-07-09 18:14 ..
[B]drwxrwx---  7 root plugdev 16384 2007-06-23 19:00 Data_1
[email]root@fossil:~/.Tras[/email]h# ls -la /media/hdd1/.Trash-me/Data_1/[/B]

As soon as we knew the name, the directory could be deleted.

---

