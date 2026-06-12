---
title: "Help on errow when starting Synaptic package manager"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by edwardzafra on 2006-05-26
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20powerpc%20(20051012)_dists_breezy_restricted_binary-powerpc_Packages) - stat (2 No such file or directory)

omg!! what have i done!

---

### Post by Sutekh on 2006-05-26
You've done nothing wrong.

You don't have the installation CD in the drive, and the Synaptic Package Manager is looking for it.

If you don't ever plan to install packages from the CD you can stop Synaptic looking for it.


If you edit the file that Synaptic uses for package sources you can stop that error.

This command backs the file up and edits it.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
``` Use your user password when prompted.

When the editor opens up, all you need to do is add a # sign to the line
```
Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)
``` so it looks like this
```
# Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)
``` 
Now the CD is 'commented out' and will be ignored from now on.

Then save the file (Ctrl+O) and exit (Ctrl+X).  Then run
```
sudo apt-get update
``` To refresh the packages sources.  You won't get this error again.

---

### Post by edwardzafra on 2006-05-27
i have done that and now im getting new error..
E: Malformed line 1 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by edwardzafra on 2006-05-27
ouch! now i get this error 

what have i done ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by aysiu on 2006-05-27
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by edwardzafra on 2006-05-27
vlad@Appoloin:~$ sudo apt-get update
E: Malformed line 1 in source list /etc/apt/sources.list (dist)
vlad@Appoloin:~$ cat /etc/apt/sources.list
deb cdrom:# Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy ma in restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted univer se multiverse
 deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-backports main restricted un iverse multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
vlad@Appoloin:~$
vlad@Appoloin:~$ sudo apt-get update
vlad@Appoloin:~$ sudo nano /etc/apt/sources.list

---

### Post by Sutekh on 2006-05-27
[quote=edwardzafra]
deb cdrom:# Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy ma in restricted[/quote] My fault. I wasn't specific enough.  *The # must be at the beginning of the line*

> **#** deb cdrom: Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy main restricted

---

### Post by edwardzafra on 2006-05-27
thanx sutek your the best:neutral:

---

