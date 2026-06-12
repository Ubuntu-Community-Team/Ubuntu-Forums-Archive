---
title: "maple 9.5"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-07-29
Hi, I am now just Maple 9.5 away from getting my machine set up exactly as I want it to be, I have a (legal) CD from my university of Maple 9.5 that is Linux compatible, however I don't know how to install it, it has a shell script that you are supposed to execute but when I do this by double clicking on it, it does nothing. If I click and say run in terminal it flashes the terminal and then it just vanishes. Please, please, please can someone help me with this, this is the only package I really really need to install!

Calv

---

### Post by Joey French on 2006-07-29
I have Maple 9.5 installed here, and working fine for a while now. If it is a shell script, you can use 
```
sudo sh /name/of/file
```
and it should do fine. If this does not get it going, I have some questions: Are you using the triple-boot CD? Do you have the install script on your box? 

Good luck!
Joey French

---

### Post by calvinthomas on 2006-07-29
Yes I am using the triple boot CD-Rom, all I have done is put the CD in my drive and tried to double click it, I tried your command and it said no such file or directory, do I have to tell it where to look? I don't know how to do that! i.e. I don't know how to tell it to look at my cd-rom! I'm a total noob as you can probably tell!

Calv

---

### Post by Joey French on 2006-07-29
Okay, let me look at my CD...
Insert CD, get icon on the desktop. then open a terminal, and type 
```
sudo sh /cdrom/installMapleLinuxSU
```
and that's it. I just did it with mine, so it should work fine for you.

---

### Post by calvinthomas on 2006-07-29
Ok, thankyou for that, that seemed to be working until I got this.....

Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.8351/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

I am in AMD64 version of ubuntu if that is necessary to know, any ideas what to do?

Calv

---

### Post by Joey French on 2006-07-29
Yes, that is a problem. I do not know if you can run Maple 9.5 in ubuntu 64. Maybe someone else will chime in, because I am not sure. I am using 32bit at the moment.

---

### Post by calvinthomas on 2006-07-29
I'm tempted to just install the 32bit OS instead of the 64bit one but I don't really know how to just overwrite it over the top and I don't want to ruin it so unless I knew exactly how to do it i'd rather have a solution with how to sort it in ubuntu AMD64

Calv

---

### Post by Kilz on 2006-07-29
> **calvinthomas said:**
> I'm tempted to just install the 32bit OS instead of the 64bit one but I don't really know how to just overwrite it over the top and I don't want to ruin it so unless I knew exactly how to do it i'd rather have a solution with how to sort it in ubuntu AMD64

Calv

[Google is your friend]("http://www.ubuntuforums.org/archive/index.php/t-159790.html") You could also try ```
sudo linux32 sh /cdrom/installMapleLinuxSU
```

---

### Post by Joey French on 2006-07-29
Interesting... I'm guessing that would compile it for 64-bit? I've never done this, let me know what happens.

---

### Post by calvinthomas on 2006-07-29
Thankyou for responses, I don't see a solution on that forum thread you sent only the same problem, am I missing something, the code you told me to try gives the same error as before!

Calv

---

### Post by bmcage on 2006-08-04
for Maple 9.5 on 64 bit linux: s
see my reply in thread [http://ubuntuforums.org/showthread.php?p=1337016](http://ubuntuforums.org/showthread.php?p=1337016)

---

### Post by calvinthomas on 2006-08-06
Well i've now switched to 32bit and installing Maple was easy! It just went straight on, however I thought i'd update to 9.52 (don't really need to its just nice to have all the fixes and things) but when I go to the terminal (after downloading) and type:

sudo sh ./Maple952LinuxUpgrade.bin

I get an error message saying:
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

/tmp/install.dir.7089/Linux/resource/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

Anyone know how I can fix this?

Calv

---

