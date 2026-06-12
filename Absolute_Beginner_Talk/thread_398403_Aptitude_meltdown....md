---
title: "Aptitude meltdown..."
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Beach on 2007-04-01
I have been fighting with Aptitude all night...  I finally had to boot on the install CD and fsck my disk, which solved my Aptitude file lock issue.  Now when I try to install anything I get the following errors.  

> sudo apt-get install rar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  unrar
The following NEW packages will be installed:
  rar
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
Need to get 0B/262kB of archives.
After unpacking 516kB of additional disk space will be used.
(Reading database ... 
dpkg: serious warning: files list file for package `gdm' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `bzip2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `bug-buddy' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `busybox-initramfs' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/rar_1%3a3.6.0-0ubuntu1~edgy1_i386.deb (--unpack):
 unable to open files list file for package `libmono0': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/rar_1%3a3.6.0-0ubuntu1~edgy1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have tried to re-install the packages listed above but I keep getting the same errors.  Anyone have any ideas?  I hate to have to reinstall the OS...

---

### Post by Nythain on 2007-04-01
sounds like whatever fsck did might have jacked your system pretty bad but i dont know for sure cause im totally unfamiliar with your errors.

for future reference whenever you have a file lock problem with aptitude, make sure there are no programs running that use aptitude (synaptic and adept) and the commands
sudo dpkg --configure -a
sudo aptitude clean

those two together usually fix most issues with aptitude being locked for various reasons

---

### Post by Beach on 2007-04-01
Thanks for the reply.   Yes, running fsck was my last resort.   I booted into recovery mode first and still could not resolve the file lock issue.   I could not even read the "/var/lib/apt/lists' directory, I would received the following error: 

ls: memory exhausted 

The "lock" file in '/var/lib/aptitude' had some crazy permissions, and it was about 3.2gb in size.  Needless to say I could not delete it.  

Then I found several posts listing the "dpkg --configure -a" trick which did nothing for me.

I thought I was home free when fsck found the errors on the drive and fixed them.  I was able to do a 'apt-get update' which I could not do before.   System still runs fine, I just can not install anything now. ](*,)

---

### Post by zvacet on 2007-04-01
I don´t promisse anything but try 
```
sudo aptitude update
```
```
sudo aptitude upgrade
```
When you installing whit aptitude you get package and all dependencies that goes with it.With apt-get you just get package and not dependencies.That is reason why is better to install with aptitude.Try

```
sudo aptitude install rar
```

---

### Post by Beach on 2007-04-01
Aptitude wants to update my Beryl if I do a "aptitude upgrade".  Last time I did this it messed up my desktop candy.  :)

I still get the same errors if I try to do a "aptitude install rar"

thanks for the reply...

---

