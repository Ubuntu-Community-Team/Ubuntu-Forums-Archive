---
title: "[SOLVED] external hard drive"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by ravendiana on 2007-08-13
My system keeps insisting my external hard drive is write only

I could have sworn that it's worked properly in the past, but then most of what I've been doing is importing flies so I'm not Totally sure.

I'm running Dapper Drake at the moment.  device manager reads it as an unkonw USb mass storage device.

it is NTFS and I can pull files off just fine and it works in windows just fine.  I presume there is a driver I need, so I need to look for it...

help?

Diana

---

### Post by Wim Sturkenboom on 2007-08-13
Standard write support for NTFS in Linux is not reliable. Not sure if it's in the Dapper repositories, but look for ntfs-3g and install it; it's my understanding that it can write reliable.

---

### Post by carloslosgrande on 2007-08-13
[FONT="Comic Sans MS"]Hi Diana, try right clicking on the icon and then select 'properties' owner may be 'root'
If so, you change it in the terminal........check>  man chown first to get the right syntax, I do it like this > sudo chown <my user name> /media/<name of the drive>[/FONT]

---

### Post by ravendiana on 2007-08-13
I am the owner of the drive,  installing ntfs3g does not seem to be working...

```
diana@omnus:~$ gksu ntfs-config
sudo: ntfs-config: command not found
diana@omnus:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g
```

---

### Post by Arthur Archnix on 2007-08-13
Look [here]("http://ubuntuforums.org/showthread.php?t=217009"). You're on dapper, so the deb has to be added to your repo. Link has details.

---

### Post by ravendiana on 2007-08-13
I did look there  when I tried it wouldn't let me  gave me the following error

```
diana@omnus:~$ gksu gedit /etc/apt/sources.list

(gedit:8750): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
```.

I get a source list file popping up telling to to "uncomment" a bunch of lines, but I don't know what that means or where to do it

Diana

---

### Post by Arthur Archnix on 2007-08-13
sorry, but there doesn't seem to be any need here for gksu. Just do sudo and your error should dissapear.
```
sudo gedit /etc/apt/sources.list
```
paste this to the bottom:
```
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) dapper main main-all
```
save, close, then
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ntfs-3g
```
Then plug your external drive in and see if you can create a folder on it.

---

### Post by ravendiana on 2007-08-13
ok  this time it worked better, but I get to the last step and get 

```
diana@omnus:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g
```

---

### Post by Arthur Archnix on 2007-08-13
Strange, that means it can't find a package matching that name in the repo you added. I don't have dapper so I can't trial and error this for you. Ok, delete that line you just added to /etc/apt/sources.list
and put this one in its place:
```
deb http://flomertens.keo.in/ubuntu/ dapper main main-all
```
save and close, then:
```
wget http://flomertens.keo.in/ubuntu/givre_key.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install ntfs-3g
```

---

### Post by ravendiana on 2007-08-13
ok that got further...  I was installing it, it looked almost done and I got this error

```
creating fuse device node...
/sbin/MAKEDEV: don't know how to make device "fuse"
dpkg: error processing fuse-utils (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libfuse2 (2.6.3-0givre2) ...

Setting up libntfs-3g1 (1.417-1) ...

dpkg: dependency problems prevent configuration of ntfs-3g:
 ntfs-3g depends on fuse-utils (>= 2.6); however:
  Package fuse-utils is not configured yet.
dpkg: error processing ntfs-3g (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fuse-utils
 ntfs-3g
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have been having dependanciey errors getting my printer running too, and the dependancy is on a file I Know I installed....

one of my friends says Dapper is my problem and I should upgrade to fawn...  but I'm afarid that will rebreack the things I have gotten to work!!!!

---

### Post by carloslosgrande on 2007-08-13
Hi, Feisty is actually easier to setup than Dapper. And the NTFS you want is in Feisty's Add/Remove programs application, a piece of cake.

---

### Post by por100pre1 on 2007-08-13
As a workaround you could format that HDD to FAT32. The only issue is that you wouldn't be able to handle files larger than 4GB with a FAT32 format.

---

### Post by ravendiana on 2007-08-13
it's a 300 gb drive with lots of large flies on it  fat32 is not an option

My only worries about fiesty are that I'll lose some of the fiels/fixes I've got so far

---

### Post by Arthur Archnix on 2007-08-13
Let's give solving the dependency issues a try before getting you to switch to another OS ;-)

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fuse-utils ntfs-3g
```

```
If that doesn't work, try:
apt-get remove fuse-utils ntfs-3g
apt-get install fuse-utils
apt-get install ntfs-3g
```

Stop at the point you get errors and post the output back here.

---

### Post by ravendiana on 2007-08-14
WOOT!

first fix did it!  I have my external back!!!!  YAY  3rd problem down!  just the printer and my NWN saves to go (for now)

Thanks!!!!

---

