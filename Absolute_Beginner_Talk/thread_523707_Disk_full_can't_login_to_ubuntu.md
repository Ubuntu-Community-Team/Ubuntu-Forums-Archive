---
title: "Disk full can't login to ubuntu ?"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-08-12
Hi!
My disk is full and because of that I cant manage to log on to ubuntu.
Please help me fast!

---

### Post by basilwatson on 2007-08-12
Me to !!!

I am using gnome partitioner to resize my partitions hopefully that will do it 

See my other thread GDM locked me out 

Stephen

---

### Post by the_axiom on 2007-08-12
I cant log in how will I use Gnome partitioner?
But I'm in rescue mode now, but I do not understand anything..

---

### Post by ThrobbingBrain66 on 2007-08-12
> **the_axiom said:**
> I cant log in how will I use Gnome partitioner?
But I'm in rescue mode now, but I do not understand anything..

You can use the Ubuntu LiveCD or if you have a spare computer, burn the gparted LiveCD
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by the_axiom on 2007-08-12
Unfortunally I do not have burning hardware in my laptop. Isn't there any way to remove files in the rescue mode? How much space do I need to free?

---

### Post by forestpixie on 2007-08-12
Use the livecd you installed with

---

### Post by cwmoser on 2007-08-12
I've encountered this problem and in my case there was a log file that ate up all the free disk space.  

What I did was:

1)  boot off the Ubuntu installation CDROM (i.e. a "live CD")
2)  mount the hard drive --- ex:  sudo mount /dev/sda3 /media/sda3
3)  cd to the root of the mounted drive -- ex:  cd /media/sda3
4)  cd to the logs folder - ex:  cd  ./var/log
5)  ls -l to see which *.log files have grown huge
6)  rm the culprit log file.
7) df -h /media/sda3 to see if there is enough free space
8)  boot  normally

Carl

---

### Post by forestpixie on 2007-08-12
if you haven't got the disc still try cleaning the apt-get cache

sudo apt-get clean

and hope that's enough room

---

### Post by the_axiom on 2007-08-12
> **forestpixie said:**
> if you haven't got the disc still try cleaning the apt-get cache

sudo apt-get clean

and hope that's enough room

Worked fine!
Thank you very much! :)

---

### Post by forestpixie on 2007-08-12
glad it helped - I should have a tidy up now then :)

---

### Post by jspangler on 2007-08-12
I found that I had this problem when I scheduled a regular backup on an external drive. At one of the times, the drive was off, and the backup proceeded to fill up the mount point on the root drive. I had to delete the backup file in this case from the live cd. So consider that as well.

---

### Post by basilwatson on 2007-08-12
> **cwmoser said:**
> I've encountered this problem and in my case there was a log file that ate up all the free disk space.  

What I did was:

1)  boot off the Ubuntu installation CDROM (i.e. a "live CD")
2)  mount the hard drive --- ex:  sudo mount /dev/sda3 /media/sda3
3)  cd to the root of the mounted drive -- ex:  cd /media/sda3
4)  cd to the logs folder - ex:  cd  ./var/log
5)  ls -l to see which *.log files have grown huge
6)  rm the culprit log file.
7) df -h /media/sda3 to see if there is enough free space
8)  boot  normally

Carl

Can you delete all the log file or do they serve a purpose?   other than to tell you what u did 

I can see some big files there which I would like to move!!!


Stephen

---

### Post by dscherry on 2007-08-12
Hi,
You still ought to find out if one (or more of the logs grew to a huge size).  If you have a runaway app that is adding log entries by error, you're just going to have the same problem again, soon.  But next time, the apt cache will already be clean, and you won't be able to clear it again.

But if it turns out all the logs are normal, then you still should do some partition work, to get a little breathing room.  

Post back the results of a 'df' command, which will show the percentage of use for each partition, and you'll be able to get some recommendations about how to handle it.

Dan

---

### Post by forestpixie on 2007-08-12
> **basilwatson said:**
> Can you delete all the log file or do they serve a purpose?   other than to tell you what u did 

I can see some big files there which I would like to move!!!


Stephen

Not sure - don't think so but are they as big as you're apt cache?

> **dscherry said:**
> Post back the results of a 'df' command, which will show the percentage of use for each partition, and you'll be able to get some recommendations about how to handle it.

Dan

It'd help if you did this

---

