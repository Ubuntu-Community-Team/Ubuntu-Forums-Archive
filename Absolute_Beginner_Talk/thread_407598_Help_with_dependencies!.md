---
title: "Help with dependencies!"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by cAllison on 2007-04-12
Ok, I've had a major problem trying to set up a freeRADIUS server on Kubuntu. The biggest problem.. I have no clue what I am doing :)

I tried to install a .tar.gz version of the software with no luck. So I tried the .rpm version only to run into more frustration. But thanks to the wonderful forums here and tons of great Ubuntu/Debian documentation I finally think I have figured out the biggest problem. Trying to:

```
sudo rpm -i freeradius-1.1.5-3.1.i586.rpm
```

I get this error in return:

```
error: Failed dependencies:
        /usr/sbin/useradd is needed by freeradius-1.1.5-3.1.i586
        /usr/sbin/groupadd is needed by freeradius-1.1.5-3.1.i586
        insserv is needed by freeradius-1.1.5-3.1.i586
        sed is needed by freeradius-1.1.5-3.1.i586
        fillup is needed by freeradius-1.1.5-3.1.i586
        coreutils is needed by freeradius-1.1.5-3.1.i586
        python is needed by freeradius-1.1.5-3.1.i586
        /bin/sh is needed by freeradius-1.1.5-3.1.i586
```

Can someone please help me! I have no idea how/where to get these.

---

### Post by teaker1s on 2007-04-12
Okay firstly we use .**deb packages** I'm guessing your using **alien** to install? if your trying to install an rpm on a debian system without **alien** installed then it's not going to work.
correctly if at all. Can you get sorce to compile or just rpm?

I'm guessing your running without gui?
this then mean you can either
```
 sudo aptitude
```
or
```
sudo apt-get install ****
``` **** remove and put package name in place

---

### Post by bcmiller on 2007-04-12
I normally would type the names of the dependancies into synaptic to see if they are there and then intall them.  If not you can search for them and install them as you are trying to install this server.

umm the answer above mine is much better...

---

### Post by SoggyCornflake on 2007-04-12
> **cAllison said:**
> Ok, I've had a major problem trying to set up a freeRADIUS server on Kubuntu. The biggest problem.. I have no clue what I am doing :)

I tried to install a .tar.gz version of the software with no luck. So I tried the .rpm version only to run into more frustration. But thanks to the wonderful forums here and tons of great Ubuntu/Debian documentation I finally think I have figured out the biggest problem. Trying to:

```
sudo rpm -i freeradius-1.1.5-3.1.i586.rpm
```
.

One of the great things about Debian Based distros is their use of deb packages rather than rpm packages.

use the following to install:```
sudo apt-get install freeradius
```

Apt-get will take care of the dependencies. :D

---

### Post by Sef on 2007-04-12
```
sudo apt-get install freeradius
```

Actually ```
sudo aptitude install freeradius
``` is better.  Aptitude is a more user friendly than apt-get.

---

### Post by cAllison on 2007-04-12
> **teaker1s said:**
> Okay firstly we use .**deb packages** I'm guessing your using **alien** to install? if your trying to install an rpm on a debian system without **alien** installed then it's not going to work.
correctly if at all. Can you get sorce to compile or just rpm?

I'm guessing your running without gui?
this then mean you can either
```
 sudo aptitude
```
or
```
sudo apt-get install ****
``` **** remove and put package name in place

Thanks for the info, I tried to get a .deb but they do not have one availible.

When I try to follow the instruction @ 3. on: 
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

I get the following errors:
```
chris@RADIUS-Kubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done

```
which i assume is normal, then:
```
chris@RADIUS-Kubuntu:~$ sudo aptitude install alien
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
**No candidate version found for alien**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

I get this when also trying to *sudo aptitude install build-essential* or.. actually anything else I've tried to install this way.

I can only imagine I'm just not doing something right, but I have no idea what it is >_>

---

### Post by Sef on 2007-04-12
Ahh...you're running Kubuntu.  In that case type this instead:

```
kdesu aptitude install freeradius
```

---

### Post by cAllison on 2007-04-12
> **Sef said:**
> Ahh...you're running Kubuntu.  In that case type this instead:

```
kdesu aptitude install freeradius
```
 Thanks sef, still having problems though, tried this and it didnt work, tried the same method to get alien, and same thing happens.

```
chris@RADIUS-Kubuntu:~$ kdesu aptitude install freeradius
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Reading package lists... 0%
Reading package lists... 100%
Reading package lists... Done

Building dependency tree... 0%
Building dependency tree... 0%
Building dependency tree... 50%
Building dependency tree... 50%
Building dependency tree

Reading state information... 0%
Reading state information... 6%
Reading state information... Done

Reading extended state information... 0%
Reading extended state information

Initializing package states... 0%
Initializing package states... Done

Building tag database... 0%
Building tag database... Done

Couldn't find any package whose name or description matched "freeradius"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

chris@RADIUS-Kubuntu:~$ kdesu aptitude install alien
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Reading package lists... 0%
Reading package lists... 100%
Reading package lists... Done

Building dependency tree... 0%
Building dependency tree... 0%
Building dependency tree... 50%
Building dependency tree... 50%
Building dependency tree

Reading state information... 0%
Reading state information... 6%
Reading state information... Done

Reading extended state information... 0%
Reading extended state information

Initializing package states... 0%
Initializing package states... Done

Building tag database... 0%
Building tag database... Done

No candidate version found for alien
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... 0%
Writing extended state information... 1%
Writing extended state information... Done

```

TIA for any more help >_>!

---

### Post by compmodder26 on 2007-04-12
Something doesn't seem right with your sources.list.  Please post the contents of it here (file is located at /etc/apt/sources.list)

---

### Post by cAllison on 2007-04-12
I dont have that exactly..........o.O
I have a /etc/apt/sources.list.d
and a ../sources.list_backup
which contains:

```

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

---

### Post by compmodder26 on 2007-04-12
hmm... seems very odd that you don't have sources.list.  That is probably to problem.  Try copying the file you posted to sources.list:

```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```

Then update:
```
sudo apt-get update
```

Then try to install the sotware you were wanting to install again
```
sudo apt-get install <package_name>
```

Where <package_name> is the name of the package to install.

---

### Post by cAllison on 2007-04-12
Thanks! Seems like the ball is rolling again, still getting no package found when I try to *sudo apt-get install freeradius* or *kdesu apt-get install freeradius* or same using aptitude, but I was able to get alien so it seems something is working now :)

---

### Post by compmodder26 on 2007-04-12
freeradius is in the universe repositories.  So you need to uncomment (remove the "#") the universe lines in your sources.list (middle of file).  Then "sudo apt-get update", then "sudo apt-get install freeradius".

---

