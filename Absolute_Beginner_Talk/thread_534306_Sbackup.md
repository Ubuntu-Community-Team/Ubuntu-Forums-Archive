---
title: "Sbackup"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Namingishard on 2007-08-25
First let me say that I did search the forums and read everyone of the search results with no luck,
I did not see this (Exact) problem anywhere.

I am running 7.04 Feisty 

Sbackup starts up fine, I change my settings(I kept the directory for the backup at default /var/backup.), I save those settings and then hit "Backup Now!"
and I get the 

"A backup run is initiated in the background. The process id is: ####"

With the System Monitor open i see Sbackupd is in Zombie status

When I run it through the command line I see
```

"I: Upgradeing to v1.3: /var/backup/2007-08-24_23.40.10.218945.ryan-namingishard.ful
Traceback (most recent call last):
  File "/usr/sbin/sbackupd", line 404, in <module>
    upgrader.upgrade_target( target, purge )
  File "/usr/sbin/upgrade_backups.py", line 60, in upgrade_target
    self.upgrade_tdir( target+"/"+adir )
  File "/usr/sbin/upgrade_backups.py", line 81, in upgrade_tdir
    self.upgrade_v13( tdir )
  File "/usr/sbin/upgrade_backups.py", line 107, in upgrade_v13
    flist = gnomevfs.read_entire_file( tdir+"/flist" ).split( "\n" )
gnomevfs.NotFoundError: File not found"

```
Donno what that means.

Also in one of the other threads someone said that the backup folder has to be made by root, what does that mean exactly? 
When I try and make the folder with mkdir it says permission denied
and when I open the Sbackup recover it says "Some of your backups are in an old backup format.
Do you want to upgrade them?"
If I click yes nothing happens.

Don't know if I gave enough info.

---

### Post by mikeyphi on 2007-08-25
Have a look under synaptic, latest version of sbackup should be 0.10.3-0.1
If it looks as though that is what you have - go for a reinstall.

It works fine for me - but I do use a specified destination rather than the default.

---

