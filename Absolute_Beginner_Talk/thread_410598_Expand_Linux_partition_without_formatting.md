---
title: "Expand Linux partition without formatting?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by supazio on 2007-04-15
I recently installed Xubuntu 6.10 (80GB drive, 50GB MSW, 20ish Xbnt) and managed to get all the things I wanted working working. Then I decided to free up some space on the Windows partition, only to learn that practically all of the space taken up on the partition is made up of things I want in the ext3 partition, but they won't fit. Is it possible to expand the ext3 and shrink the ntfs partitions without formatting either?

---

### Post by speeves on 2007-04-15
Here is an article which discussed the GParted Live CD:
[http://www.linux.com/article.pl?sid=06/04/25/1917228](http://www.linux.com/article.pl?sid=06/04/25/1917228)

and how it can be used to resize your partitions.  Here is the GParted homepage:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

with links to the live CD.  Beware!! Back up your data before proceeding...

---

### Post by saphil on 2007-04-15
How many of these have you played with?  I tested and blew up probably 20 linux installations before I felt secure with running a Linux-only box.  Recently I purged my last windows box and went entirely to Linux.  The only thing that had been holding me back was a bunch of stuff in MS Publisher..  I changed companys and that stuff became unneccesary - and I discovered scribus - so I took the plunge.  

Theoretically, what you want to do is possible.  gparted is the partitioning  tool to try.  You can get it by using synaptic search in synaptic for gparted or typing 
```
sudo apt-get install gparted 
```you may already have it loaded on your linux-side 
try 
```
locate gparted
which gparted
```or 
```
apt-get search gparted
```There is a yawning possibility of this not working, however.  I would suggest backing up all the stuff you are moving, then defrag your windows partition so all the data in the partition is toward the front.  Then  set a system-restore point on the windows side.  Then go into the linux side and open gparted and resize the windows partition.  This should work.  restart the pc to see if the windows side still boots.  This is fixable if it doesn't (probably) but you don't want to take it on faith.  
When you see the windows partition is booting properly, go back to the linux side and use gparted to stretch the linux partition.  
make sure both sides boot properly.
if yes, then you are done.  if not, you may have to work on your grub files, and I am not entirely sure how you would proceed.  I would certainly help as much as possible.

ntfs is not very friendly to manipulation, and I haven't had lots of luck with sizing partitions after the fact.  This is not intended to be THE authoritative answer for your question, but a friendly suggestion that probably won't result in your system being hosed.

yours,
Wolf

---

### Post by supazio on 2007-04-15
Thanks for the help. Is gparted already on the Xubuntu/Ubuntu live cds(I'm out of CD-Rs and don't want to buy more if I don't need to)?

---

### Post by speeves on 2007-04-16
Yes, it is on the Ubuntu LiveCD.  BTW, you will need to use the Live CD anyways, because you won't be able to manipulate the partitions if you are running off of the hard drive.

---

