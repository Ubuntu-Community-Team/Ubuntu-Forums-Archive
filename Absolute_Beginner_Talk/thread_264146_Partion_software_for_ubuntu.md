---
title: "Partion software for ubuntu?"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by maxM on 2006-09-24
Hi, I got trouble with my windows partition and need to format it. But I can't get into windwos, and the Ubunutu Dapper install tool can't make NTFS partitions. So does anyone have a tool that I can use to format the partiotion and make it NTFS from Ubuntu?

Thanks for replies, regards from me.

---

### Post by bulldog on 2006-09-24
Use the windows cd-rom to make NTFS partitions.

---

### Post by ronmarley1 on 2006-09-24
gparted is sorta like Partition Magic.  It's in the repos.

---

### Post by maxM on 2006-09-24
Nope, that doesn't work. I tried to use the repair utility so every time I start the PC with the Win XP cd it freez at "34 min. until finished".. and nothing happens if I trie to start windows normaly... so I need a program for ubuntu that can make NTFS partitions

---

### Post by bulldog on 2006-09-24
> **maxM said:**
> Nope, that doesn't work. I tried to use the repair utility so every time I start the PC with the Win XP cd it freez at "34 min. until finished".. and nothing happens if I trie to start windows normaly... so I need a program for ubuntu that can make NTFS partitions

Make it FAT32 with gparted and when you install windows reformat NTFS.

Look's like a disk error, let windows do a chkdsk before install.

---

### Post by ronmarley1 on 2006-09-24
gparted does NTFS

---

### Post by maxM on 2006-09-24
what am I doing wrong? I use the code: sudo apt-get install gparted and everything seems to be alright, but I can't find the program (to run it). I belive it's a command that makes programs apear in Applications>Accessories... anyone cares to give it to me :)

---

### Post by bulldog on 2006-09-24
It should be in administration.

but sudo gparted in terminal will do.

---

### Post by ronmarley1 on 2006-09-24
EDIT: I got beat to the punch, again!
After installing, you have two choices:
1. From a terminal, type ```
sudo gparted
``` (it requires root privelages).
Or
2. Go to System-->Administration-->Gnome Partition Editor.  If you choose this way, it will then ask for your password.

Typing ```
man gparted
``` in a terminal window will open the manual.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) has a bunch of information on gparted

---

### Post by maxM on 2006-09-24
Yes I found it, but when I trie to create a new partition I can't choose NTFS. Why?

[img]http://img162.imageshack.us/my.php?image=screenshotzo0.png[/img]

---

### Post by CupofDice on 2006-09-24
I just used gparted for the first time (to turn 10 gig into ext3). When you apt-get install gparted, it gives you the suggestion of installing ntfsprogs and hfsutils. ```
sudo apt-get install ntfsprogs
``` and see how that works.

Some info - [http://packages.debian.org/stable/otherosfs/ntfsprogs]("http://packages.debian.org/stable/otherosfs/ntfsprogs")

---

### Post by CatKiller on 2006-09-25
> **maxM said:**
> Hi, I got trouble with my windows partition and need to format it. But I can't get into windwos, and the Ubunutu Dapper install tool can't make NTFS partitions. So does anyone have a tool that I can use to format the partiotion and make it NTFS from Ubuntu?

Thanks for replies, regards from me.

Not quite what you're after, but you seem to have already got responses suggesting that you use gparted, which is the best option for Ubuntu. As an alternative, most hard drive manufacturers have applications that you can download to check or partition your drive from a boot floppy. Might be worth checking out if you struggle with gparted. Oh, and the Ubuntu Live cd already has gparted on if you fancied doing it that way.

---

