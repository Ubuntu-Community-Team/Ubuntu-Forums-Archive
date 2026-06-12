---
title: "disk usage analysis"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by mspendlo on 2007-02-08
Hi

I need a little help analysing my disk usage on edgy. 

The disks are as follows :

[/dev/hda2] / = 10GB
[/dev/hda6] /home = 2GB
[/dev/hda1] /windows =  12GB
[/dev/hda5] /data = 45GB

I ran out of disk space on / but the diagnostics seem to show that I am only using 5GB or so :

matt@matt-laptop:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              11G  9.9G  153M  99% /

If I check in baobab and I exclude /data and /windows it shows me :

"10.6 GB (used 9,9GB available 709 MB)"

But the GUI tool only accounts for 5GB max. So whats eating the rest ??

Any help appreciated..

---

### Post by aysiu on 2007-02-09
Try [FileLight](http://www.methylblue.com/filelight/). It's in the Universe repositories.

First of all, get rid of the installer files for all your programs. Those are probably taking up space: ```
sudo aptitude clean
``` That command deletes all the .deb files in /var/cache/apt/archives

Next, make sure you have extra repositories enabled by following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Finally, install FileLight: ```
sudo aptitude update
sudo aptitude install filelight
``` I think you can run it with the command... *filelight*

---

### Post by mspendlo on 2007-02-09
> **aysiu said:**
> 
First of all, get rid of the installer files for all your programs. Those are probably taking up space: ```
sudo aptitude clean
``` That command deletes all the .deb files in /var/cache/apt/archives

Finally, install FileLight: ```
sudo aptitude update
sudo aptitude install filelight
``` I think you can run it with the command... *filelight*

Thanks for the tips, I cleaned up aptitude and installed filelight but it just shows me the same as baobab - i.e. that I am using 2.2GB on / yet somehow I am still using 9.9GB of my drive ?

I am obviously missing some fundamental understanding. I've attached a screenshot displaying the current state.

Any further tips or advice ?

TIA

---

### Post by ComplexNumber on 2007-02-09
i suggest that discrepancy is caused by boabab not being able to read the contents of various large files or directories because it can only read directories where you have read access. 

go to the command line and type in 'gksudo baobab', then run the program.

---

### Post by Michaelt74 on 2007-02-10
Msplendo, have you recently done a system backup using System>Administration>Backup
If you have that's most likely where the problem is as Ubuntu backs up all your stuff and eats your hard drive space. 

Try this if you have:
Applications>Accessories>Terminal, sudo aptitude clean (cleans out archives).

sudo du -sh /* (shows file space usage by application)

My disk eater was 8.2G /var, I needed more information so I typed in sudo du -h /var and got this:

7.9G /var/backup/2007-01-22_22.11.51.797882.michael-laptop.ful (the disk eater)

To remove it I typed in the following (still in the terminal) all on one line:

sudo rm -r /var/backup/2007-01-22_22.11.51.797882.michael-laptop.ful

That erased the problem, and now I’m back with 10G of additional space on my drive.

---

### Post by mspendlo on 2007-02-10
ok - my main error was not running the command line diagnostics with sudo thereby not seeing the whole picture so it follows that the GUI tools would require gksudo to see the whole picture (as an aside gksudo baobab errors with "Failed to open session DBUS connection" - just made do with sudo du).

I guess this is was my fundamental misunderstanding !

As Michaelt74 alluded to, it was backups hogging the space in /var/lib/backuppc. I'd installed backuppc a whiel ago and not configured it properly before removing it.

Back down to 80% available :)

Thanks for all the tips.

---

### Post by ComplexNumber on 2007-02-10
**mspendlo**
i assumed that most of the "missing" space would be found in  /root/.Trash because it can't be read if sudo(or gksudo for graphical applications such as boabab) isn't used.

---

