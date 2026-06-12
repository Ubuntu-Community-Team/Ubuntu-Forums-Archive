---
title: "Failed to execute child process &quot;cdrdao&quot;"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by domeboy on 2008-01-30
I try to play or rip cds and this is what I get:

Failed to execute child process "cdrdao" (No such file or directory).

I can't get DVDs to play either. Can this be related?

---

### Post by jan quark on 2008-01-30
this might help
just read the dvd section
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by jan quark on 2008-01-30
and check with this code
```
rpm -q cdrdao

```

if the cdrdao is installed on your system

---

### Post by domeboy on 2008-01-30
I ran that in the terminal and this is what I got:

bink@bink-laptop:~$ rpm -q cdrdao
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Name index using db3 - No such file or directory (2)
package cdrdao is not installed
bink@bink-laptop:~$ sudo apt-get install cdrao
[sudo] password for bink:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by domeboy on 2008-01-30
I ran that from the terminal

I tried a DVD in Mplayer and Totem and this is what I get: 

Totem could not play 'file:///media/cdrom0/VIDEO_TS/VTS_01_1.VOB'.

---

### Post by jan quark on 2008-01-30
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
this error usually pops up when another installation or update application is running 
close all synpatic, update and install applications and run only the synaptic package manager and search for cdrdao not cdrao
> bink@bink-laptop:~$ sudo apt-get install cdrao
cdrdao 
typos are dangerous in case sensitive systems

---

