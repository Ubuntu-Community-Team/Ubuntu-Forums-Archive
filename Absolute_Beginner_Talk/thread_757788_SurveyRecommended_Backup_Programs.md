---
title: "Survey:Recommended Backup Programs"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by JBA2337 on 2008-04-17
I wanted to find out which backup programs are used and most recommended by the users of Ubuntu Forums, so I did a search for "backup" and "best backup".

The following is an unscientific survey that I did of about 300 messages on the Ubuntu Forums, where the writer of the post recommended a specific backup program for use with Ubuntu. They are listed in order, most recommended first.

                  Ranking*
	     (higher = better)                                  
	                                                               
tar	                  8                                                
rsync	                8                                                 
partimage            7                                                
quickstart	       6                                               
sbackup	              4	                                                               
grsync	               4                                                
remastersys        3                                                
timevault	      2                                              
clonezilla     	       2                                                
backup manager  1                                          
bacula	               1
mondo/mindi	   1
backuppc	     1

*survey of about 300 messages on the ubuntu forums, completed 3/15/08.

number = number of persons who recommended program, out of the messages where a specific program was recommended.


JBA2337

---

### Post by Hendrixski on 2008-04-17
That's an interesting list, I've only really tried rsync, and I know I should use it more often, I just ..., well, I don't.  It's stupid of me, but I just plane old-fashioned copy files onto an external drive.

---

### Post by dca on 2008-04-17
rsync and backuppc.

---

### Post by northern lights on 2008-04-17
```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media
```

simple & efficient - if you can do without an extra app, why would you want one more? Opinions may differ - just my 2 cents...

---

### Post by dje on 2008-04-17
I use (and recommend ;)) my new project linbaku (see blue link in my sig), basically a frontend for making tar backups

dje

---

### Post by JBA2337 on 2008-04-17
To dje:

I installed linbaku, just as you described in [http://code.google.com/p/linbaku/](http://code.google.com/p/linbaku/). The installation went as you predicted, but when I click on the linbaku icon, nothing happens.
I completely uninstalled the program using the Synaptic Package Manager, and then I reinstalled it using Synaptic. But it still does not work. I am using Ubuntu 7.10 on a Toshiba laptop computer. 

Any other ideas?

JBA2337

---

### Post by sawjew on 2008-04-20
I thoroughly recommend [Flyback]("http://code.google.com/p/flyback/").  Simple to use, only backs up changed files, can restore any version and can be automated.

Excellent tool.

---

### Post by Tews on 2008-04-20
Ive been using Quick-Start from day 1 and have NEVER had a problem with it .. :)

---

### Post by quirks on 2008-04-20
For backup of my personal files I use **rdiff-backup** ([http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)). Usage is as easy as it can only be:
```
rdiff-backup /src/dir /backup/dir
```
It automatically creates incremental backups, so I can also restore files a deletes months ago, without wasting much space. It also supports compression and bandwidth-saving backup over the network.

As for my my operating system, I do a complete filesystem backup with the good old **dump **utility. It has built-in compression and allows for extraction of single files from the backup, so I don't have to restore the complete backup, when I'm only interested in one file (in contrast to partimg, for example).

---

### Post by herdivet on 2008-05-06
I have used backuppc for about eight months, backing up two laptops and two desktops onsite, one desktop at a remote location.  It worked flawlessly until I upgraded to Hardy.  I am researching here to see if anyone else has solutions for getting it working on Hardy.  

I like it because I can set the time frame for backing up each PC, then just foreget about it, and every day it backs up all the systems.  Some need backed up during the night. others during the day.  Two are windows (I just back up the date in My Documents and below) and three are ubuntu where I backup all the home files.

---

### Post by eivind on 2008-05-13
Of the few I've tried, my very short list would be (in order of preference)

rdiff (once you find out how to use the options)
slbackup (Skolelinux backup. A bit clumsy, but works)

... and finally, sbackup last, because it can create non-working backups without giving the user any notice:

[https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719](https://answers.launchpad.net/ubuntu/+source/sbackup/+question/30719)

---

