---
title: "[SOLVED] Restoring from a Win XP backup file"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by RayArdia on 2008-03-11
Can I restore files backed up from a previously installed XP system? Files have the extension .bkf. and are currently on my Phillips 227GB external hard disk.
When I try to open the .bkf backup folder Ubuntu tells me that there's no auto method for handling the files.

---

### Post by forrestcupp on 2008-03-11
You can't restore Windows backups in Ubuntu.  You're in the wrong forum.  [Tech-Forums](http://www.tech-forums.net/pc/f9/) is a great forum to ask Windows questions in.

---

### Post by forestpixie on 2008-03-11
there's a program - mtftar which can convert to a .tar if that's any help

[http://ubuntuforums.org/showthread.php?t=349158](http://ubuntuforums.org/showthread.php?t=349158)

this is the [file]("http://gpl.internetconnection.net/files/mtftar.tar.gz")

Galician?

---

### Post by RayArdia on 2008-03-11
> **forestpixie said:**
> there's a program - mtftar which can convert to a .tar if that's any help

[http://ubuntuforums.org/showthread.php?t=349158](http://ubuntuforums.org/showthread.php?t=349158)

this is the [file]("http://gpl.internetconnection.net/files/mtftar.tar.gz")

Galician?
No, not Galician, English living in Galicia! Have downloaded mtfr but don't really follow how to use it. In the Readme file it refers to mtfr used as a filter as in " mtftar < MyBackup.bkf | tar xvf - " but I'm too much a NEWB to know what to do!

---

### Post by RayArdia on 2008-03-11
[QUOTE=forrestcupp;4496943]You can't restore Windows backups in Ubuntu.  You're in the wrong forum.  [Tech-Forums](http://www.tech-forums.net/pc/f9/) is a great forum to ask Windows questions in.[/QUOTE
Thanks for response, but yours seems "at odds" with Forestpixie's. I really need those files but don't want anything more to do with that nice Mr Gates!

---

### Post by forestpixie on 2008-03-11
wouldn't know how to use it unfortunately, sorry, but at a guess - if you copy the backup file to the desktop, making sure you have more than 1 copy of it justin case, and then cd Desktop - you could

mtftar *nameofbackup.bkf* | tar xvf -

I have many friends living in Galicia - my ex's family are from Santiago - not that they're friends, but those that still talk to me :) - spent 3 weeks in a small 2 horse village near Vigo couple of years back - great place.

As far as the post by forrstcupp goes - you would not believe how many - help me with windows problems turn up here - not even slightly ubuntu orientated - I just assumed that you were trting to read the file.

---

### Post by RayArdia on 2008-03-12
> **forestpixie said:**
> wouldn't know how to use it unfortunately, sorry, but at a guess - if you copy the backup file to the desktop, making sure you have more than 1 copy of it justin case, and then cd Desktop - you could

mtftar *nameofbackup.bkf* | tar xvf -            .........................

.................

Many thanks, tried that but with only partial success. Have tried to copy what results in Terminal (I [U]know[U] there's a way of taking a screenprint, but can't re-find it!)

ray@Study:/tmp/mtftar$ cd Desktop
bash: cd: Desktop: No such file or directory
ray@Study:/tmp/mtftar$ cd
ray@Study:~$ mtftar RA Full 28 Nov 2007.bkf | tar xvf - 
bash: mtftar: command not found
ray@Study:~$ cd/tmp
bash: cd/tmp: No such file or directory
ray@Study:~$ cd /tmp
ray@Study:/tmp$ cd /mtftar
bash: cd: /mtftar: No such file or directory
ray@Study:/tmp$ 
ray@Study:/tmp$ ls
ButlerTable.pdf       ior             mtftar.tar.gz   Tracker-ray.5559
ContemporaryLamp.pdf  keyring-6BiAFO  orbit-ray       virtual-ray.zYCo9T
gconfd-ray            mapping-ray     orbit-root
gconfd-root           mtftar          ssh-QtfayJ5390
ray@Study:/tmp$ cd /mtftar.tar.gz
bash: cd: /mtftar.tar.gz: No such file or directory
ray@Study:/tmp$ 
ray@Study:/tmp$ 

Can't seem to get much further!
BTW we live about an hour's drive N of Vigo on the peninsula of O Grove. Remember the New Forest very well, we used to caravan to the Forestry Commission site fairly central, as I remember and we walked just about _everywhere_!
Back to the problem - have the file (called RA Full 28 Nov 2007) in Desktop, have tried to 
open it, but of course get :-
No application suitable for automatic installation is available for handling this kind of file.
Any further helpful suggestions?	](*,)

---

### Post by glennric on 2008-03-12
First you will have to extract and install the file mtftar.tar.gz.
It appears you put this file in your home directory.  So type
```
cd #to make sure you are in your home dir
tar xzvf mtftar.tar.gz
cd mtftar
make
sudo cp mtftar /usr/bin/
```
Then try
```
mtftar RA Full 28 Nov 2007.bkf | tar xvf -
```

---

### Post by glennric on 2008-03-12
By the way, before you can make mtftar you will need to install the package build-essential with
```
sudo apt-get install build-essential
```

---

### Post by RayArdia on 2008-03-12
Thankyou. Tried that, Terminal shows:-
ray@Study:~$ cd/home
bash: cd/home: No such file or directory
ray@Study:~$ tar xzvf mtftar.tar.gz
tar: mtftar.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
ray@Study:~$ sudo apt -get install build-essential
[sudo] password for ray:
sudo: apt: command not found
ray@Study:~$ 
Still :confused:

---

### Post by glennric on 2008-03-12
First, type things exactly as I give them.  Try cut and paste for accuracy.  I looked closer at what you had before and the tar file is in the /tmp dir not your home dir.
Try
```
sudo apt-get install build-essential
cd /tmp
tar xzvf mtftar.tar.gz
cd mtftar
make
sudo cp mtftar /usr/bin/
```
then 
```
cd /path/to/bkf/file
mtftar filename.bkf | tar xvf -
```
Change /path/to/bk/file to the actual path to the bkf file, and filename.bkf to the actual name of the bkf file.

---

### Post by forrestcupp on 2008-03-12
> **RayArdia said:**
> [QUOTE=forrestcupp;4496943]You can't restore Windows backups in Ubuntu.  You're in the wrong forum.  [Tech-Forums](http://www.tech-forums.net/pc/f9/) is a great forum to ask Windows questions in.
Thanks for response, but yours seems "at odds" with Forestpixie's. I really need those files but don't want anything more to do with that nice Mr Gates![/QUOTE]

Sorry, I thought you were trying to actually restore a backup.

Your current problem is that you tried to type cd/home and you should just type cd

---

### Post by RayArdia on 2008-03-12
> **glennric said:**
> First, type things exactly as I give them.  Try cut and paste for accuracy.  I looked closer at what you had before and the tar file is in the /tmp dir not your home dir.
Try
```
sudo apt-get install build-essential
ftecd /tmp
tar xzvf mtftar.tar.gz
cd mtftar
make
sudo cp mtftar /usr/bin/
```
then 
```
cd /path/to/bkf/file
mtftar filename.bkf | tar xvf -
```
Change /path/to/bk/file to the actual path to the bkf file, and filename.bkf to the actual name of the bkf file.
So far so good, with your help! Got this in Terminal - what next please?

ray@Study:/tmp/mtftar$ cd /home/ray/Desktop
ray@Study:~/Desktop$ mtftar RA Full 28 Nov 2007.bkf | tar xvf -
Usage: mtftar [-v] [-p] [-s setno] [patterns...] < backup.btf | tar xvf -
       mtftar [-v] [-p] [-s setno] -f backup.btf [patterns...] | tar xvf -
       mtftar [-v] [-p] [-s setno] -f backup.btf -o output.tar [patterns...]
       mtftar [-v] [-p] [-s setno] -o output.tar [patterns...] < backup.btf
       mtftar -l [-v] [-s setno] < backup.btf
       mtftar -l [-v] [-s setno] -f backup.btf
       mtftar -L [-v] [-s setno] < backup.btf
       mtftar -L [-v] [-s setno] -f backup.btf
ray@Study:~/Desktop$

Afternote:- typing ls gave me:
ray@Study:~/Desktop$ ls
RA Full 28 Nov 2007.bkf  rhinefet_5.08_2.6.19.patch
Readme.pdf               via_lan_driver_v5.08_appnote_ver0.8.tar.gz
ray@Study:~/Desktop$ -

So I'm still not really a lot further forward!

---

### Post by RayArdia on 2008-03-18
Still trying - with my limited know-how :confused:!
Terminal shows:-

ray@Study:~/Desktop$ ls  RA Full 28 Nov 2007.bkf
ls: RA: No such file or directory
ls: Full: No such file or directory
ls: 28: No such file or directory
ls: Nov: No such file or directory
ls: 2007.bkf: No such file or directory
ray@Study:~/Desktop$ 
 Can anyone help me open (and use) this .bkf file please?

---

