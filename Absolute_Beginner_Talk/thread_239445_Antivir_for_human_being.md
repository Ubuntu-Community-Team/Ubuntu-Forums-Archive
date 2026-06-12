---
title: "Antivir for human being"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Tibor60 on 2006-08-19
I thought seriouly Ubuntu for human being... I have Dapper installed and I thought a good idea to scan from linux my windows partitions for viruses. I first tried to install clamav...installed normally, but freshclam give an error: OUTDATED version, go to the clamav site for the new version. Ok, I downloaded it, and tried to install from source. No success, the configure script exited with error message "C compiler could not create executables"
(gcc installed of course, the version which goes with Dapper.)
Ok, let's see Avira Antivir... you need the dazuko engine. The version with Dapper is outdated, ok, go to the dazuko site. Documentation say you you have to be familiar with compiling the kernel. ok, I am not, go to an other site. F-prot antivir... try to compile from debian package, dependency problems with configure script, the missing packages can not fount by apt-get. The same with compiling from source.

Can somebody recommend me any antivirus software which I can install with no pain, not going in compiling the kernel, reachable for "human being?"

---

### Post by Perfect Storm on 2006-08-19
Check some of the howto:

[http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)

[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

---

### Post by statue on 2006-08-19
I recommend [F-prot]("http://www.f-prot.com"). It is extremely easy to install using apt-get....i believe it was just apt-get install f-prot......or maybe it was aptitude i used...either way it is very easy to install and it works great...though antivirus for linux is kind of overkill anyway...i believe there are less than 100 known viruses for linux, all of which are extrememly rare. I understand your paranoia though with the dual boot, I am the same way as I also am dual booting and want AV just to make sure with things I download. Better safe than sorry....

---

### Post by orb9220 on 2006-08-19
Well one problem with scanning from linux a ntfs winxp partition is you  won't be able to do anything if you find it.

Since linux does not have write capabilities to a ntfs partition. you will not be able to delete the offending virus anyway.

And since windows viruses are becoming quite sophisicated and advanced virus programs are having a hard time keeping up. Especially linux based ones.

I would not trust a linux antivirial program since they do not appear much in the way of keeping up to date. They do not seem to be in a hurry on this.

For windows I would recommend nod32. It's not free but always have found the free antiviri programs to be lacking in the detection area.

---

### Post by Perfect Storm on 2006-08-19
Well, if you use Panda Desktopsecure for linux, you'll get dailey updates which you can use to scan windows.
But it's not free (in both sense).

---

### Post by Tibor60 on 2006-08-19
statue: it is not installable with apt-get. From source...the problem is the same as I told in the 1. message....but of course I think f-prot is good if I can install by anyway...

tibor@GOLDEN10:~$ sudo apt-get install f-prot
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package f-prot
tibor@GOLDEN10:~$ sudo apt-get install F-prot
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package F-prot
tibor@GOLDEN10:~$ sudo apt-get install fprot
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fprot
tibor@GOLDEN10:~$ sudo apt-get install Fprot
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package Fprot
tibor@GOLDEN10:~$

---

### Post by statue on 2006-08-19
try: 

sudo aptitude update

then...

sudo aptitude install f-prot

---

### Post by Tibor60 on 2006-08-19
statute: thanks, with aptitude I could install f-prot with sucess!

---

