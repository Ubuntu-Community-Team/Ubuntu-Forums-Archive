---
title: "Whats Using My Disk Space?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by opticyclic on 2006-08-06
My hard disk is filling up fast and I don't know what with!
```
andrew@Ubuntu:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
**[COLOR="Red"]/dev/sda4             9.4G  7.8G  1.2G  87% /[/COLOR]**
varrun                252M   68K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  116K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-23-386/volatile
/dev/sda1              41G   17G   24G  42% /media/C_win
/dev/sda6              19G  6.2G   13G  33% /media/D_doc
/dev/sda7              19G  3.2G   15G  18% /media/E_dev
/dev/sda8              26G  2.5G   23G  10% /media/F_games
/dev/sda5             7.0G  4.0G  3.1G  56% /media/FAT32
andrew@Ubuntu:~$      
```

I had Gnome on Breezy, then I upgraded to Dapper and added KDE.
There seems to be an awful lot of updates now though (nearly everyday).

I haven't been doing much at the moment exept browse the web and tweak the interface so there shouldn't be too much in my home directory.
However, there is 3.3 Gb in there (!) and I can't work out what it is without traversing every directory and looking at the size.

There is a nice application for Windows that shows you graphically what is taking up space on your hard drive.
[http://www.win.tue.nl/sequoiaview/](http://www.win.tue.nl/sequoiaview/)

Is there anything similar for Linux?

---

### Post by catlett on 2006-08-06
/dev/sda4 is not just your home directory it is your entire directory. / is the symbol for root. If you didn't make seperate partitions for home or any other system feature then everything is on the root partition.
3.3gb is about normal for a linux distro with 2 window managers insatalled.
Someone else will have to give you the way to see what is where.

---

### Post by opticyclic on 2006-08-06
Is there a command that I can run that will recursively output the size of every directory?

---

### Post by Stew2 on 2006-08-06
I had a similiar problem a few weeks ago. Check out the thread I started on it. The file light program is nice and gives a graphical representation of what files are using up most of your disk space.
Hope it helps, it helped me :D

[http://www.ubuntuforums.org/showthread.php?t=221521](http://www.ubuntuforums.org/showthread.php?t=221521) 

Regards,
Stew2

---

### Post by opticyclic on 2006-08-07
The info from your thread is really helpful.
> **moma said:**
> $ cd $HOME

Show size of directories
$ du -h 

Show size of files
$ du -ha

For more info
$ man du
---------------------

Find all files >= 4Mb
$ cd $HOME
$ find . -size +4M
$ find . -name "*mp3" -size +4M -ls
----------------------

Filelight is the sort of thing I was looking for too. Thanks!

Is it safe to remove Gnome-Desktop?

---

### Post by opticyclic on 2006-08-12
KDirStat is another program that can show you where your disk space has gone.
It is in the repositories and also looks like SequoiView with the rounded bubble blocks etc
[http://kde-apps.org/content/show.php?content=10159](http://kde-apps.org/content/show.php?content=10159)

---

