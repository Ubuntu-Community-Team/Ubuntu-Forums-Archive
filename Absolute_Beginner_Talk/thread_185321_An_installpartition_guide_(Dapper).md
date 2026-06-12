---
title: "An install/partition guide (Dapper)?"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by mc510 on 2006-05-31
From what I read, it sounds like a good idea to create a separate home partition, but (rank beginner that I am) I'm not too confident about using the manual partition tool during the install process ... and I don't know what if any additional steps are involved in install/reinstall with separate home partition.  Is there a newbie-oriented guide to this process anywhere?  Searched the wiki and forums but found nothing that's dumbed-down enough.

---

### Post by PriceChild on 2006-05-31
I don't really like the idea of being able to store your home on another partition.

Maybe it is better in allowing linux to be reinstalled without losing all your home files... but i backup and restore it anyway so i'm fine.

If there's such a big problem that you need to reinstall ubuntu, then not only are loads of settings transferred in ".<<something>>" files and folders in your home dir, but so too are any errors in them which may have annoyed you.

You should be able to live without :)

---

### Post by Jagot on 2006-05-31
This site runs you through the text mode install method of creating a separate /home partition:

[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm)

---

### Post by Lil_Eagle on 2006-05-31
One thing to seriously keep in mind if you do create a separe home partition is that if you install more than one version of linux on your computer (for example a breezy partition and a dapper partition) then if you point both of them to the same home partition the settings will be the same for both systems.

That can lead to serious problems if one system has more recent versions of software (such as KDE or Gnome).  Settings that work fine in one version may not work so well in others.

Worse yet, if you try another distro that has done modifications to the software, they can corrupt your lovely (k)ubuntu!

It is very handy to have all your data on another partition, but it's just as easy to do a backup before you do something so drastic.  It's a good idea to do regular backups anyway.  That's a good reason to have a DVD-RW or even better, a remote machine to back up to.

Got an old machine lying around?  Install Breezy on it and network it to your main PC and send the backups to it.  It only needs to be on when you want to do the backup, although you can also use it as a print server or firewall.  There's always a reason to use it

Remember, Ubuntu will run fine on an old 386, although Gnome might be slow, you don't need a Desktop for any of the functions I mentioned.  You really don't even need a monitor once it's configured.

---

### Post by aysiu on 2006-05-31
I used to have a separate /home partition, but I kind of like doing fresh installs every six months, seeing what the new Ubuntu default looks like, and then customizing it how I like... again.

Now I have a separate data partition so I won't have to copy it all back from backups.

I do back up my ~/.mozilla and ~/.thunderbird folders, though, of course.

This is a tutorial on creating a separate /home partition, in case anyone's interested:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

