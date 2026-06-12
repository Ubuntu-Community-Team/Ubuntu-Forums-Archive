---
title: "pr0blems after i reinstalled ubuntu"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by dragnazz5.0 on 2006-08-15
well i went ahead and ref0rmatted my c0mputer and g0t rid 0f wind0ws because i havent used it in m0nths and i needed m0re r00m f0r linux.  but n0w i cant get my c0mputer back t0 where it was.  either i just g0t stupid and f0rg0t everything 0r i just cant find it.  im trying t0 install firestarter firewall and mplayer with all the c0decs that i need.  ive tried everything and it d0esnt seem t0 w0rk at all.  im still very new t0 this thing since i d0nt ever use terminal 0r anything 0ther than the internet (id actually like t0 find a linux versi0n that is just the internet and gaim and maybe a few 0ther things, but i d0nt think there is 0ne).  when i try t0 0pen synaptic package manager i get this err0r

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

d0nt kn0w what that means but i cant find anything that i need.  i cant even install kaffeine.  thanks f0r any help

0h yeah, my "o" key rarely w0rks s0 ive reverted t0 using the zero key because its easier than hitting o ten times.  sorry if its hard to read

---

### Post by Kobalt on 2006-08-15
The 0 thing is ok :)
At first, try typing in a terminal 
```
sudo gedit /etc/apt/sources.list
``` then give your admin password and a text file should appear. Copy/paste it here please, so that we can check if there's anything wrong with it. 
Also, while you're in command line, try typing : 
```
sudo aptitude update
``` and tell us what it gives you. 

And also, the error message you gave us mention Breezy : are you running Ubuntu 5.10 or 6.06 ? (Breezy or Dapper?)

Cheers !

---

### Post by dragnazz5.0 on 2006-08-15
im using 5.10


this is the first 0ne-

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that so
ftware in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

this is the sec0nd 0ne-

mike@mike:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release [30.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages [585kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources [232kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources [1454B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Fetched 855kB in 9s (91.5kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

---

### Post by Kobalt on 2006-08-15
Ok. If you want to install more softwares, you might want to activate Universe and Multiverse repositories. To do so, remove the "#" in front of the corresponding lines, so that your file should look like this : 

> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that so
ftware in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

You can edit the file by the command I've given you before (sudo gedit /etc/apt/sources.list)

Then run a 
```
sudo aptitude update
```
and a 
```
sudo aptitude upgrade
```

You should find much more softwares with synaptic now :)
Out of curiosity, why not using the newer version of Ubuntu ?

Cheers !

---

### Post by dragnazz5.0 on 2006-08-15
well i decided t0 g0 ahead and switch t0 6.06, ill have t0 change the rep0sit0ry thing and see if i cant get that t0 w0rk

---

### Post by dragnazz5.0 on 2006-08-15
well i decided t0 g0 ahead and switch t0 6.06, ill have t0 change the rep0sit0ry thing and see if i cant get that t0 w0rk

i did everything y0u said and i still cant play vide0s. it w0nt let me install m0zillap-mplayer

---

