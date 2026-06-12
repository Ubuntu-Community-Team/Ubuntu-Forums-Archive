---
title: "Synaptic, apt-get, and automatix: all broken AND novel wireless problem"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by typ3 on 2007-03-28
I've been using Ubuntu Dapper Drake for a week and I'm in love with it, but it seems that I can't install any software. 

I was able to install software from the DVD that came with my Ubuntu Unleashed perfectly using Synaptic, but unlike before, I cannot install anything using apt-get, synaptic or even automatix. 

Obviously this is really frustrating as I can't get the software I need to do stuff and this being a new install, I need to install a lot of stuff. 

So how do I fix this? Do I have to change the servers I'm connecting to or something? (PS: My normal internet works when I'm trying to install stuff, I'm not that much of a n00b)

ALSO

I installed network manager, but it stopped my previously working wireless from working (I have an Orinoco card). I uninstalled it using synaptic and now my wireless works but in a weird way: 

When I turn on my laptop the wireless doesn't work until I go into the network settings and just look around. All of the network settings stuff is disabled: I do it all using iwconfig and iwlist. Plus my wireless stuff doesn't work after I come out of hibernation. 

What do I do to fix this problem?

---

### Post by h0ax on 2007-03-28
Need a little more details on the apt-get problem..  Maybe you could post the output of the command.

Occasionally, sources will go down in /etc/apt/sources.list and they need to be removed/commented out.

Maybe this will help you, but we can't tell if we don't know what kind of errors you have

---

### Post by typ3 on 2007-03-28
Synaptic says this when I try to install mplayer

> mplayer:
 Depends: libartsc0 (>=1.5.2-0) but it is not installable
 Depends: libdvdread3  but it is not installable
 Depends: libmad0 (>=0.15.1b) but it is not installable
 Depends: libmpcdec3  but it is not installable
 Depends: libungif4g (>=4.1.3) but it is not installable
 Depends: libxvmc1  but it is not installable


Apt-get says this:

> 
The following packages have unmet dependencies:
  mplayer: Depends: libartsc0 (>= 1.5.2-0) but it is not installable
           Depends: libdvdread3 but it is not installable
           Depends: libmad0 (>= 0.15.1b) but it is not installable
           Depends: libmpcdec3 but it is not installable
           Depends: libungif4g (>= 4.1.3) but it is not installable
           Depends: libxvmc1 but it is not installable


What do I do?
E: Broken packages
[/QUOTE]

---

### Post by seshomaru samma on 2007-03-28
can you post your sources .list?
```
cat /etc/apt/sources.list
```
and whats the output of :
```
lsb_release -a
```

---

### Post by h0ax on 2007-03-28
Looks like you need some dependencies
have you tried getting the things it says it depends on individually?

ie, sudo apt-get libartsc0 
as one example?

---

### Post by typ3 on 2007-03-28
I'll try that. I just thought that Synaptic grabbed the dependencies automatically?

As for the sources.list

> 
cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531.2)]/ dapper main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe



#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
#AUTOMATIX REPOS END


As for the lsb_release -a output:

> 
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper


Thanks for the help. 

Brandon

---

### Post by jackrobinson on 2007-03-28
> **typ3 said:**
> Synaptic says this when I try to install mplayer



Apt-get says this:



What do I do?
E: Broken packages


try:
```
sudo apt-get -f install
```

---

### Post by seshomaru samma on 2007-03-29
sudo apt-get -f install might work
if not comment out (put a # infront of it) this line:

```
deb http://www.getautomatix.com/apt dapper main
```
in your /etc/apt/sources.list

then run 
```
sudo apt-get update
```
and
```
sudo apt-get install mplayer
```

---

### Post by jackrobinson on 2007-03-29
> **seshomaru samma said:**
> sudo apt-get -f install might work
if not comment out (put a # infront of it) this line:

```
deb http://www.getautomatix.com/apt dapper main
```
in your /etc/apt/sources.list

then run 
```
sudo apt-get update
```
and
```
sudo apt-get install mplayer
```
commenting out the automatix repository will NOT help.. why does this stupid paranoia grip people whenever they see the automatix repository? The packages mentioned all come from the ubuntu repositories.

---

### Post by compiledkernel on 2007-03-31
Automatix is unsupported software by the community. These forums do not support it either. If you have further difficulties with Automatix, you should refer back to their forums at [www.getautomatix.com](www.getautomatix.com) for further help.

Let me firmly reiterate that Automatix is just as it is --

"automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu."

---

