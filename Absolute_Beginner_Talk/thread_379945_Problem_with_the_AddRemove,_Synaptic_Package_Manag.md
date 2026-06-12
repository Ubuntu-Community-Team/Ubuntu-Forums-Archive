---
title: "Problem with the Add/Remove, Synaptic Package Manager and the Update Manager"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Diego- on 2007-03-09
Hello, i'm using Ubuntu 6.06 LTS and everything was working fine, but now when i execute the Add/Remove, the Synaptic Package Manager or the Update Manager it just closes it (it starts loading and lasts a second), i think it closes it when is printing: "Dependency Generation"

Thanks, and sorry my english.

---

### Post by igknighted on 2007-03-09
Try typing "sudo apt-get update" and "sudo apt-get upgrade" in the terminal.  Post back any errors.

---

### Post by Diego- on 2007-03-09
The update:
"Reading package lists... Done"

The upgrade:
Reading package lists... Done
Segmentation faulty tree... 50%

Thanks.

Edit with some more info:
The Add/Remove closes when printing: "Dependancy generation"
The Update Manager when printing: "Bulding dependency tree"
The Synaptic Package Manager closes when the loading bar is about 40%
Everything else seems to work fine...

---

### Post by igknighted on 2007-03-09
> **Diego- said:**
> The update:
"Reading package lists... Done"

The upgrade:
Reading package lists... Done
Segmentation faulty tree... 50%

Thanks.

Wow...

did anything happen to your system around when this started?  Failed install/successful install/anything?

---

### Post by Diego- on 2007-03-09
> **igknighted said:**
> Wow...

did anything happen to your system around when this started?  Failed install/successful install/anything?
No, nothing wrong, i was working, reading and learning, I even succesfully ported a program i made in windows... i remember the last thing i installed was the "Memory Profiler" and then tried to download something else, and this problem started... The Memory Profiler works btw

Thanks.

---

### Post by igknighted on 2007-03-09
can you post the results of "sudo cat /etc/apt/sources.list"?  Its a shot in the dark, but maybe theres an error there.  I have never seen apt just segfault like this.  You might want to run "fsck /dev/<your ubuntu partition>" (probably /dev/hda#) to make sure the file system isnt corrupted.

---

### Post by Diego- on 2007-03-09
> **igknighted said:**
> can you post the results of "sudo cat /etc/apt/sources.list"?  Its a shot in the dark, but maybe theres an error there.  I have never seen apt just segfault like this.  You might want to run "fsck /dev/<your ubuntu partition>" (probably /dev/hda#) to make sure the file system isnt corrupted.

Sources.list
```

deb http://ar.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ar.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ar.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://ar.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ar.archive.ubuntu.com/ubuntu/ dapper-backports main restricted univer se multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ dapper-backports main restricted un iverse multiverse

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe


```

I can't get the fsck to work, i'll keep trying, i'm just too new at this.

Thanks.

---

### Post by igknighted on 2007-03-09
type "sudo fdisk -l" to list all your partition, then "sudo fsck <partion identified as ext3 in prev command>"

I see nothing abnormal in your sources.list aside from the "couldn't be verified by installer" lines, but nothing looks *wrong*

---

### Post by Diego- on 2007-03-09
I did again the apt-get update and it downloaded some stuff, then i ran the apt-get upgrade and worked fine :D (everything is working now).  I still don't know what the problem was...
The fsck seemed to work fine...

Thank you

---

### Post by igknighted on 2007-03-09
Try running "sudo apt-get clean && sudo apt-get autoclean" if the problem ever comes back

---

### Post by okkie on 2007-08-29
Type '‘deb' is not known on line 57 in source list /etc/apt/sources.list
E: The list of sources could not be read.
anybody know what this is please,synaptic package manager gone

---

### Post by okkie on 2007-08-29
sudo apt-get clean && sudo apt-get autoclean was run in terminal.sorry cannot read list.how do i install linux restrictedmodules 2.6.20.16?

---

