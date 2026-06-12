---
title: "Is there a System Restore feature for Ubuntu?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by Cherry Popper on 2006-07-03
Ok, I went looking in the How-To/Hardware forums and saw some folks talking about enabling Vista-like transparency in Ubuntu and I'd like to give it shot but since I only have about 8 hours of Ubuntu experience, I'm sure I'll break something.

So here's my half-baked plan, break something ... restore. Break something ... restore, till I get it right. Everyone has to start somewhere right?

In WinXP, you could set a restore point before doing anything and if it doesn't work, just restore to an earlier point and try again.

Is there a similar feature for Ubuntu? :)

---

### Post by TheMono on 2006-07-04
Not to the best of my knowledge - I'd reccomend, before you do that, that you learn the basics of the command line (specifically the ls, cd, mv and cp commands), and keep backups of any files you change. As long as you can use those 4 commands and "sudo", you should be able to reverse anything you do.

---

### Post by mzembe on 2006-07-04
up to a point, I guess you could log in as a different user and start over from there.

---

### Post by MaximB on 2006-07-04
there are some programs to make a full backup - even to a hole partition
if you afraid to mess up thing I'd recommend you to do a FULL backup first.

---

### Post by Jagot on 2006-07-04
Ubuntu doesn't have the function built in, but you could make a backup with something like these:

[http://www.mondorescue.org/](http://www.mondorescue.org/)
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by MaximB on 2006-07-04
[QUOTE=Jagot]Ubuntu doesn't have the function built in, but you could make a backup with something like these:

[http://www.mondorescue.org/](http://www.mondorescue.org/)
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)[/QUOTE]
if you refered to my pose...you can add this function in the add/remove programs

---

### Post by lapsey on 2006-07-04
i wish it did. personally i keep a list of all the stuff i've installed onto the base system.

if i am doing anthing funky i first back up my home directory:

tar -czf ~/Desktop/myhomebackup.tar.gz --exclude=*/Desktop/* --exclude=*/.Trash/* --exclude=*/.thumbnails/* --exclude=.rnd --exclude=*/.gdesklets/* --exclude=*/.vmware/* --exclude=*/vmware/* --exclude=*/lmms/* ~/ ;

that does everything except folders with those names in them. feel free to remove or add --exclude parameters

it's quite easy to restore from that backup, if you lose your home directory for whatever reason. all your settings should be restored.

---

### Post by H.E. Pennypacker on 2006-07-30
System Restore would be a great addition to Ubuntu (or any Linux distro).  It is critical, because many people make mistakes they should never make.  It happens, and asking people to create a disk image is far too complicated for the average person.  I am sure I could manage creating a disk image, lots of people couldn't.

Windows System Restore is not nearly as difficult as creating a partition image.  You simply add a note to the restore point, and Windows takes care of the rest.  It's really a two or three step process, and it's all graphical.  

If only something like this was available.

---

### Post by Frank Golden on 2006-07-30
> **H.E. Pennypacker said:**
> System Restore would be a great addition to Ubuntu (or any Linux distro).  It is critical, because many people make mistakes they should never make.  It happens, and asking people to create a disk image is far too complicated for the average person.  I am sure I could manage creating a disk image, lots of people couldn't.

Windows System Restore is not nearly as difficult as creating a partition image.  You simply add a note to the restore point, and Windows takes care of the rest.  It's really a two or three step process, and it's all graphical.  

If only something like this was available.
Partimage a part of the Linux SystemRescueCD
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
allows you to make a "byte by byte" image of your Ubuntu
install and saves it to the media of your choice. I keep
an image of my Ubuntu partition on a external USB HDD.
In the event of disaster it only takes about 30 minutes to 
restore this image and be back in business.
It is complicated but with proper instruction most people
can do it. I can run through the process from my head after doing
it a few times and I am still fairly new to Linux.
The tutorial from psychocats
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)
explains a lot but references using partimage by installing
temporarilly in memory using the ubuntu installer. I use the SystemRescueCD which has partimage on it. I will attempt to write
a guide to using this version of partimage and post it here.
Give me some time. In the meantime learning the command line
and the terminal is a great first step in mastering Ubuntu
or linux.

---

