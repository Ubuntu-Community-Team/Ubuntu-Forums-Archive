---
title: "Urgent i cant go to my add/remove thing"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by kingvicious on 2006-08-03
when i go to applications and click on add/remove i get this error

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.


what do i do?

---

### Post by aysiu on 2006-08-03
It should be something like this: ```
kingvicious@ubuntu:/etc/apt$ ls -al
total 44
drwxr-xr-x   4 root root 4096 2006-07-24 21:51 .
drwxr-xr-x 113 root root 8192 2006-08-03 11:38 ..
-rw-r--r--   1 root root   30 2006-07-24 21:11 apt.conf
drwxr-xr-x   2 root root 4096 2006-07-24 21:14 apt.conf.d
-rw-------   1 root root    0 2006-05-30 17:51 secring.gpg
**-rw-r--r--   1 root root** 1652 2006-07-24 21:51 sources.list
-rw-------   1 root root 1200 2006-05-30 17:51 trustdb.gpg
-rw-r--r--   1 root root 2393 2006-05-30 17:51 trusted.gpg
``` I've bolded the important part. If yours doesn't look like that, then you may have to check your permissions and ownership: ```
sudo chown root:root /etc/apt/sources.list
sudo chmod 644 /etc/apt/sources.list
sudo aptitude update
```

---

### Post by kingvicious on 2006-08-03
which one are the codes i put in my terminal?

---

### Post by ColdDeath on 2006-08-03
You would run this one first:
```
ls -al
```
Then you must look at what is displayed. Look for "sources.list". If it says something like "-rw-r--r--   1 root root 1652 2006-07-24 21:51 sources.list". You'll want to run these commands:
```
sudo chown root:root /etc/apt/sources.list
sudo chmod 644 /etc/apt/sources.list
sudo aptitude update
```

This is just what aysiu said, but with the commands seperated, the credit goes to him/her :)

---

### Post by kingvicious on 2006-08-03
well i did that first command and got all of these and i couldnt find the sourcelist that u were talking bout

kingvicious@kingvicious:~$ ls -al
total 287096
drwxr-xr-x 25 kingvicious kingvicious      4096 2006-08-03 13:19 .
drwxr-xr-x  3 root        root             4096 2006-08-02 09:19 ..
-rw-------  1 kingvicious kingvicious      7270 2006-08-03 13:26 .bash_history
-rw-r--r--  1 kingvicious kingvicious       220 2006-08-02 09:19 .bash_logout
-rw-r--r--  1 kingvicious kingvicious       414 2006-08-02 09:19 .bash_profile
-rw-r--r--  1 kingvicious kingvicious      2227 2006-08-02 09:19 .bashrc
drwxr-xr-x  3 kingvicious kingvicious      4096 2006-08-03 12:44 .config
drwxr-xr-x  5 kingvicious kingvicious      4096 2006-08-03 13:14 Desktop
-rw-------  1 kingvicious kingvicious        26 2006-08-02 09:24 .dmrc
-rw-------  1 kingvicious kingvicious        16 2006-08-02 09:24 .esd_auth
-rwxr-xr-x  1 kingvicious kingvicious   8493622 2005-06-06 04:22 et-linux-2.60-u pdate.x86.run
-rwxr-xr-x  1 kingvicious kingvicious 270965248 2005-06-06 04:22 et-linux-2.60.x 86.run
drwxr-xr-x  7 kingvicious kingvicious      4096 2006-08-03 09:53 .etwolf
drwxr-xr-x  8 kingvicious kingvicious      4096 2006-08-02 19:09 .evolution
lrwxrwxrwx  1 kingvicious kingvicious        26 2006-08-02 09:19 Examples -> /us r/share/example-content
-rw-r--r--  1 kingvicious kingvicious   1004786 2006-08-03 12:09 Firefox_wallpap er.png
drwx------  4 kingvicious kingvicious      4096 2006-08-03 13:13 .gaim
drwx------  5 kingvicious kingvicious      4096 2006-08-03 13:19 .gconf
drwx------  2 kingvicious kingvicious      4096 2006-08-03 13:40 .gconfd
drwxr-xr-x 21 kingvicious kingvicious      4096 2006-08-03 12:43 .gimp-2.2
-rw-r-----  1 kingvicious kingvicious         0 2006-08-03 13:24 .gksu.lock
drwx------ 13 kingvicious kingvicious      4096 2006-08-03 13:14 .gnome2
drwx------  2 kingvicious kingvicious      4096 2006-08-02 09:24 .gnome2_private
drwxr-xr-x  2 kingvicious kingvicious      4096 2006-08-02 09:24 .gstreamer-0.10
-rw-r--r--  1 kingvicious kingvicious        93 2006-08-02 09:24 .gtkrc-1.2-gnom e2
-rw-r--r--  1 kingvicious kingvicious        32 2006-08-02 15:28 .hwdb
-rw-------  1 kingvicious kingvicious      1863 2006-08-03 13:19 .ICEauthority
drwxr-xr-x  2 kingvicious kingvicious      4096 2006-08-02 18:49 .icons
drwx------  3 kingvicious kingvicious      4096 2006-08-02 20:26 .kde
-rw-r--r--  1 root        root            10062 2006-05-01 06:11 libxxf86dga1_1. 0.0-0ubuntu3_i386.deb
drwx------  3 kingvicious kingvicious      4096 2006-08-02 14:51 .local
drwx------  3 kingvicious kingvicious      4096 2006-08-02 09:24 .metacity
drwx------  3 kingvicious kingvicious      4096 2006-08-02 09:25 .mozilla
drwxr-xr-x  3 kingvicious kingvicious      4096 2006-08-02 09:24 .nautilus
drwxr-xr-x  3 kingvicious kingvicious      4096 2006-08-02 19:26 NVIDIA-Linux-x8 6-1.0-8762-pkg1
-rw-r--r--  1 kingvicious kingvicious  13032175 2006-08-02 19:26 NVIDIA-Linux-x8 6-1.0-8762-pkg1.run
-rw-r--r--  1 kingvicious kingvicious       324 2006-08-02 19:34 .nvidia-setting s-rc
drwxr-xr-x  2 kingvicious kingvicious      4096 2006-08-02 20:26 .qt
-rw-------  1 kingvicious kingvicious      3103 2006-08-03 12:54 .recently-used
-rw-r--r--  1 kingvicious kingvicious         0 2006-08-02 10:13 .sudo_as_admin_ successful
drwxr-xr-x  2 kingvicious kingvicious      4096 2006-08-02 18:49 .themes
drwx------  4 kingvicious kingvicious      4096 2006-08-02 11:36 .thumbnails
drwx------  2 kingvicious kingvicious      4096 2006-08-03 13:14 .Trash
drwx------  2 kingvicious kingvicious      4096 2006-08-02 09:24 .update-notifie r
-rw-------  1 kingvicious kingvicious       122 2006-08-03 13:19 .Xauthority
-rw-r--r--  1 kingvicious kingvicious      2977 2006-08-03 13:27 .xsession-error s

---

### Post by vincentvee on 2006-08-03
i used to get this message with 5.10 breezy, haven't had it with 6.06, the code posted by cold death is what you need to run, the sudo code is what you need to run in your terminal buddy.good luck
ciao
:confused: sorry man, didn't read the last reply to the post......](*,)

---

### Post by aysiu on 2006-08-03
Sorry, I forgot to give you a command: ```
cd /etc/apt
``` That will get you into the right directory before you ```
ls -al
```

---

### Post by kingvicious on 2006-08-03
i got this error when i tryed those 3 codes u listed on ur secound post the first 2 didtn give any errors but the third one gave me this 

kingvicious@kingvicious:~$ sudo aptitude update
E: Type 'http://archive.ubuntu.com/ubuntu' is not known on line 33 in source list /etc/apt/sources.list
E: Type 'http://archive.ubuntu.com/ubuntu' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.

---

### Post by aysiu on 2006-08-03
Can you post the output of these commands, then? ```
cd /etc/apt
ls -al
cat sources.list
```

---

### Post by kingvicious on 2006-08-03
well thnx for the help but unfortnatlly i need to go to work right now :P mybe i can get it to work when i come back thanks for the help tho

---

### Post by kingvicious on 2006-08-03
cd /etc/apt  
kingvicious@kingvicious:/etc/apt$

kingvicious@kingvicious:/etc/apt$ ls -al
total 40
drwxr-xr-x   4 root root 4096 2006-08-03 13:25 .
drwxr-xr-x 107 root root 4096 2006-08-03 13:17 ..
-rw-r--r--   1 root root   30 2006-08-02 09:17 apt.conf
drwxr-xr-x   2 root root 4096 2006-08-02 09:20 apt.conf.d
-rw-------   1 root root    0 2006-05-30 17:51 secring.gpg
-rw-r--r--   1 root root 2236 2006-08-03 13:25 sources.list
drwxr-xr-x   2 root root 4096 2006-04-18 12:47 sources.list.d
-rw-r--r--   1 root root 2244 2006-08-03 13:25 sources.list.save
-rw-------   1 root root 1200 2006-05-30 17:51 trustdb.gpg
-rw-r--r--   1 root root 2393 2006-05-30 17:51 trusted.gpg
-rw-r--r--   1 root root 2381 2006-05-30 17:51 trusted.gpg~
kingvicious@kingvicious:/etc/apt$


kingvicious@kingvicious:/etc/apt$ cat sources.list

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
# deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
# deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
kingvicious@kingvicious:/etc/apt$

---

### Post by aysiu on 2006-08-03
Notice how just about every line starts with **#**, **deb**, or **deb-src**? That's the way it should be.

You have three renegade lines in there: ```
http://archive.ubuntu.com/ubuntu
http://archive.ubuntu.com/ubuntu
http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
``` You also seem to have some repeated lines in there.

You can get a fresh sources.list in one of these places:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by vincentvee on 2006-08-03
hey man just a thought....
go to:
applications>accessories>alacarte menu editor
check if it is ticked in the list under applications

---

### Post by bonzodog on 2006-08-03
In that list, if you look down through it, you will see that three of the lines do not begin with the word 'deb'. These lines are actually duplicated and can be erased from the file. Open a terminal and do:

```
$sudo gedit /etc/apt/sources.list
```

That will open the file in gedit. Erase those three lines that do not begin with the word 'deb'. Save the file.

then do:

```
sudo apt-get update
```
That should bring your system up to date.

---

### Post by kingvicious on 2006-08-04
well bonzodog i like ur idea but it wont let me save the file..

---

### Post by aysiu on 2006-08-04
```
sudo nano /etc/apt/sources.list
``` or ```
gksudo gedit /etc/apt/sources.list
``` will allow you to save the file. *sudo* temporarily gives you administrator privileges. ```
gedit /etc/apt/sources.list
``` alone will not allow you to save.

---

### Post by kingvicious on 2006-08-04
ayisu thank you that secound code you gave me on ur last post allowed me to save it thank you and thank everone who helped me

---

