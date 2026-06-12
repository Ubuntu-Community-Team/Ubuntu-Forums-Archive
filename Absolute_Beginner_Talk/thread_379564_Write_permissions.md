---
title: "Write permissions"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by David_UK on 2007-03-08
Dual boot WinXP and Ubuntu 6.06.

I have made a FAT32 partition so i can exchange files between OS's but trying to write to it from linux gives 'You do not have permissions to write to this folder'.  I also do not have permissions to change permissions - if that makes sense.  
I guess that my login is the problem.  How do I log in with the correct permissions?  I installed the linux, and created just one user at the installation.
Thanks.

---

### Post by taurus on 2007-03-08
How do you mount that fat32 partition?  Do you mount with by hand or do you use /etc/fstab?

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by David_UK on 2007-03-08
I used the disc manager in linux, selected the partition and mounted a folder on it.
Thanks for the link. I'll work through it and report back.

---

### Post by Patrick K on 2007-03-08
I got so fed up with dealing with permissions on my FAT32 partitions I edited fstab to  give me full permissions. 

Here is how I did it. 
Opened fstab for editing:
> gksudo gedit /etc/fstab
I found the lines with the partitons I wanted to access. Then changed "uid" and "gid" to 1000, which is my user number (and probably your's, too). I had to reboot for the changes to take effect since they were mounted. 

Now i can do anything I want to those partitions including changing permissions. I just got frustrated with dealing with this all the time. The other day I was in a creative mood and had layered some tracks on a song I'm working on. i couldn't save the file and fought with the OS for a while. Needless to say, the creative mood was quickly gone. So i decided to take control of the partitions myself.

---

### Post by David_UK on 2007-03-11
Taurus

> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Thanks, that's done the trick.  Took a couple of attempts - wasn't sure if the gaps were spaces or tabs.
Thanks for your input!

---

