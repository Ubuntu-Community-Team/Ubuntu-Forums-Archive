---
title: "Backing Up Ubuntu OS with the &quot;TAR&quot; command works partly..."
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-14
Hello ALL !!!

I have the following problem with the TAR Backup command:

1. I used the following command to create a "TAR" Backup:

tar cvpzf ubuntu_backup.tgz

--exclude=/home/dimitris/Desktop/ubuntu_backup.tgz  (<- Exclude the Backup file)
--exclude=/mnt      (<- Exclude other Hard Drives or Partitions)
--exclude=/media
--exclude=/proc
--exclude=/lost+found
--exclude=/sys /

2. To put the "TAR" Backup back inside my Ubuntu, I used:

tar xvpfz ubuntu_backup.tgz -C /


The problem is this:

When I use my Ubuntu, I like to make Backups of the installed Programs TOO !!!

Basically, I want to be able to experiment with new programs ...

IF I mess up my Ubuntu OS with some DOZENS of (non-usefull) programs, I installed (for experimental purposes), I want to be able to use the "TAR" command to install the Backup & bring my Ubuntu OS back to life (WITH it's old installed programs & therefore resulting in a (as close as a) "Brand NEW" Ubuntu install...

Right now, the "TAR" command does NOT get rid of the DOZENS of programs I experimented with...

What do I have to include (or maybe remove an "--exclude=/"), to the TAR command to SAVE programs TOO?


Thanks.

---

### Post by meborc on 2006-03-14
may be those guides will give you a clue... 

[http://ubuntuforums.org/showthread.php?t=80790](http://ubuntuforums.org/showthread.php?t=80790)
[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

EDIT: deleted some mambo-jambo that i said here... then read the howto... :)

gl :)

---

### Post by Klaidas on 2006-03-14
Maybe this will help: [http://www.linux.org/lessons/interm/c316.html](http://www.linux.org/lessons/interm/c316.html)

---

### Post by dvarsam on 2006-03-14
Thanks for your reply.

Actually the "tar" command that I used comes from one of the articles you suggested:

Article#: 81311.

I ran the tar command from my Desktop though.

Does it make a difference?

Thanks.

---

