---
title: "DVD data backup programs"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by wickstopher on 2007-01-30
Hey, there.  I was wondering if anyone knew of a good program that would allow you to back up data onto a series of dvds or cds, i.e., you specify the data that you need backed up, and then the program keeps asking you for another dvd until everything has been copied.  Any dvd copying software for ubuntu that I have found thus far has only enabled you to create one dvd at a time, and has in fact disabled dvd burning if the file queue is too large.  thanks for any help!

---

### Post by hal10000 on 2007-01-30
cdbackup is a fine commanline tool kdar is a kde-gui for backups and there are dozends of other tools that might fit your needs. Just look into your package manager.

---

### Post by greenstar on 2007-02-01
I hope I'm not stating the obvious. He means open up synaptic

System->Administration->Synaptic Package Manager

then search (there's a button in synaptic) for data backup, etc. Most packages have descriptions and homepage addresses where you can get more info.

greenstar

---

### Post by wickstopher on 2007-02-01
Yeah, I've already tried that.  Thanks, though!  Unfortunately, after installing about 15 different programs that do more or less the exact same thing, I still haven't found something that suits this particular need.  What I want is a program that enables me to easily back up my external hard drives to DVDs without having to manually break everything down into 4.7gb packages.  I specify a drive or folder to copy, and It starts copying the data, and the only thing I have to do is keep inserting DVDs when it tells me to.  Perhaps there is a way to configure GnomeBaker or some other program to do it, but anything I've tried so far won't let me burn a DVD if I've added more files than the 4.7gb capacity to the job queue.

---

### Post by hal10000 on 2007-02-02
dar or kdar does just what you want to do. In kdar there you can configure the kind of backup media and/or the amount of your "slices" to backup your data. If you choose "DVD" then it will ask you for a new DVD if the capacity of your media is full.

---

### Post by Marsolin on 2007-02-02
I'll second hal10000.  [KDar]("http://linuxappfinder.com/package/kdar") is the best option that I'm aware of.

---

### Post by wickstopher on 2007-02-02
My problem with kdar is that it is an archiving (compressing) tool, and it needs to create an archive on my hard drive before copying any of the data to DVD.  And I don't have enough space free on my hard drive to accomodate an archive of the size that I need!  I tried having the archive directory be my dvdrw drive, but it failed.

---

### Post by Marsolin on 2007-02-02
There's a program called [MultiCD]("http://linuxappfinder.com/package/multicd") that does exactly what you want with CD's. I don't know if it will work with DVD's.

---

### Post by wickstopher on 2007-08-21
I started this thread back when I first started using Ubuntu and have yet to come up with an acceptable solution to backing up my large external hard drive to a series of DVDs.  I recently decided to give kdar another try, but found that it is not available in the Feisty repositories (and when attempting to compile from source or download from the Edgy repositories, have run into dependency issues that are either unresolvable or not really worth it as far as I'm concerned, given that when I first tried kdar it wasn't really what I was looking for).

So, I implore the community once again:

I'm looking for a simple program (GUI not necessary but a simple one would be nice) to automatically back up a large (>150 GB) amount of data on an external hard drive to a series of DVDs.  Ideally, the program would simply let me select the folder/drive to be backed up, and then prompt for a DVD every time a new one is required to get on with the process.  It would also help if it checked for data integrity.  Something like Nero BackItUp (I believe that is what the application was called...it's been a long time ;) ) on windows.

multicd doesn't seem to be doing the trick.  And in 8 months of using linux, I haven't come across a single application that I once used in Windows that I haven't found an equal or better equivalent of in Linux (barring music notation software), and this seems to me like such a simple task that there has to be something out there.  But I can't find it!  Any help would be greatly appreciated.

---

### Post by wickstopher on 2007-08-23
bump?

---

### Post by greenstar on 2007-10-03
Have you tried backup2l? It's in the Universe repository.

```
sudo aptitude install backup2l
```

There's also g4l. It's a live CD based disk cloner that supports file-mode and CD/DVD burning. I just found this tonight. Looks like symantec is going to make them change the name of the project, so they might be offline for a while before long. Anyway, better get your live CD while you can. It's ± 40 MB download. Here's the link:

[http://freshmeat.net/projects/g4l/](http://freshmeat.net/projects/g4l/)

Greenstar

---

