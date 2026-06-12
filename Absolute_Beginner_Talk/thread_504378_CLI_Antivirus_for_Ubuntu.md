---
title: "CLI Antivirus for Ubuntu"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-07-19
Hello,

I would like to have an antivirus program on my ubuntu as an on-demand scanner. It would be very good if it would be command-line interface. Any ideas?

---

### Post by PaulFr on 2007-07-19
```
sudo apt-get install clamav clamav-freshclam
``` If you want a GUI, add **avscan** to that list. The CLI scanner is **clamscan** and the GUI is **avscan** (freshclam is to update your virus data).

---

### Post by O-pos on 2007-07-19
I installed it but it somehow doesn't work :(

```
 

~$ sudo apt-get install clamav clamav-freshclam
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  clamav-base libclamav2
Suggested packages:
  unrar lha clamav-docs
Recommended packages:
  arj unzoo
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam libclamav2
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.1MB of archives.
After unpacking 12.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com feisty-security/universe libclamav2 0.90.2-0ubuntu1.3 [371kB]
Get:2 http://security.ubuntu.com feisty-security/universe clamav-base 0.90.2-0ubuntu1.3 [204kB]
Get:3 http://security.ubuntu.com feisty-security/universe clamav-freshclam 0.90.2-0ubuntu1.3 [9694kB]
Get:4 http://security.ubuntu.com feisty-security/universe clamav 0.90.2-0ubuntu1.3 [870kB]
Fetched 11.1MB in 11m47s (15.8kB/s)                                            
Preconfiguring packages ...
Selecting previously deselected package libclamav2.
(Reading database ... 138691 files and directories currently installed.)
Unpacking libclamav2 (from .../libclamav2_0.90.2-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package clamav-base.
Unpacking clamav-base (from .../clamav-base_0.90.2-0ubuntu1.3_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.90.2-0ubuntu1.3_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.90.2-0ubuntu1.3_i386.deb) ...
Setting up libclamav2 (0.90.2-0ubuntu1.3) ...

Setting up clamav-base (0.90.2-0ubuntu1.3) ...
Adding system user `clamav' (UID 110) ...
Adding new group `clamav' (GID 120) ...
Adding new user `clamav' (UID 110) with group `clamav' ...
Not creating home directory `/var/lib/clamav'.
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.90.2-0ubuntu1.3); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)
~$ clamscan
LibClamAV Error: cli_loaddb(): No supported database files found in /var/lib/clamav/
ERROR: Not supported data format

----------- SCAN SUMMARY -----------
Known viruses: 0
Engine version: 0.90.2
Scanned directories: 0
Scanned files: 0
Infected files: 0
Data scanned: 0.00 MB
Time: 0.000 sec (0 m 0 s)


```

---

### Post by Outrunner on 2007-07-19
Strange... Try typing this

```
sudo dpkg --configure -a
```

---

### Post by O-pos on 2007-07-19
ok, now it works, thanks :)

---

### Post by O-pos on 2007-07-19
There is still one thing I don't understand: If I try to scan a folder with clamscan, it scans only the files which are in this folder. If this folder contains another folder (with bunch of files inside), it's content won't be scanned. Is there any option for that?

---

### Post by jordanmthomas on 2007-07-19
```
clamscan -r folder
```
I'm guessing this should work, but I haven't actually used clamav.  According to its manpage though this is what you should do.

[http://linux.die.net/man/1/clamscan](http://linux.die.net/man/1/clamscan)

---

### Post by dca on 2007-07-19
If it runs from the command line, is there a ' -R ' toggle that needs to be added?  Don't know much about ClamAV, sorry.

---

### Post by jordanmthomas on 2007-07-19
> if you select a folder everything in it will be scanned!!!
...only if you tell it to scan recursively.  This may be true in the GUI frontend avscan, but the command line version just does the contents of the folder without traversing the folders withing it.

---

### Post by FleetAdmiral74 on 2007-07-19
Just for info, the r or R (not sure which) stands for recursive I think. That makes it scan all the subdirs as well. It can be applied to other command line functions.

---

### Post by wpshooter on 2007-07-19
Can you let us know when this program finds any viruses on your system !!!

---

### Post by O-pos on 2007-07-19
it works with "-r" fine.

but the speed is somehow low. for each video file it takes more than minute and for movies - I think more than few minutes. why is that? how can one deal with it?

---

### Post by dca on 2007-07-19
Burn your music and videos to disk?
 
Due to compression of these formats I would think it'd take a heck of a lot longer to scan than say OO docs/files...   Lots of info....

---

### Post by O-pos on 2007-07-19
> **wpshooter said:**
> Can you let us know when this program finds any viruses on your system !!!

I will let know :)

regarding speed, Antivir was very quick with video and audio files. Maybe it needs certaing settings too?

---

### Post by PaulFr on 2007-07-20
Regarding clamscan speed, you may need to wait a bit (**[https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/108502](https://bugs.launchpad.net/ubuntu/+source/clamav/+bug/108502)**).

---

