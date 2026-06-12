---
title: "Can't apt-get packages"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by mandra on 2005-08-04
I have loaded up Ubuntu and so far love the distro.  What I can not figure out is why I can't apt-get the most basic packages.

I have added the extra repositories as outlined in the unoficial user guide but can not load the most basic of packages

EX:

mandra@ubuntu:~$ sudo apt-get install smeg
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package smeg

or

$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5


I have already done an apt-get upgrade which worked fine and internet connectivity is great

Thanks.

Mandra

---

### Post by grim42 on 2005-08-04
Input this command:
> sudo apt-get update. Note **update** not **upgrade** to get the new repository information.

---

### Post by GavinX on 2005-08-04
Are you absolutely sure that the extra repositories are enabled?

---

### Post by mandra on 2005-08-05
I think this is my problem...

When I "sudo apt-get update"

It connects to all the archives but then gives me this error.

W: Conflicting distribution: cdrom://Ubuntu 5.04 _Hoary Hedgehog_ - Alpha i386 Binary-1 (20050129) unstable Release (expected unstable but got hoary)
W: You may want to run apt-get update to correct these problems

Now the cdrom is not mounted and the distro I used for the install is ubuntu 5.04 from Linux Mag march 2k4.

Any ideas?

---

### Post by KingBahamut on 2005-08-05
I typically remove the CDROM from the sources.list entirely. That will correct the issue with conflicting distro.

---

### Post by mandra on 2005-08-05
^^^ thanks for the tip don't know why i didn't think of that one.

Anyway that issue is now gone the update works fine unfortunately it still doesn't work.  

EX,
mandra@ubuntu:/etc$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
 :-?

---

### Post by charlieg on 2005-08-05
Are you sure that's the right package name?  Why not use synaptic?  If you are intent on using the command line, try apt-cache to search for the package you want:
```
$ apt-cache j2re
```
Strangely, on my machine that does return a package name matching what you're trying.  Please check it does the same on yours (it might help diagnose where the problem lies).

---

### Post by GavinX on 2005-08-05
[QUOTE=mandra]^^^ thanks for the tip don't know why i didn't think of that one.

Anyway that issue is now gone the update works fine unfortunately it still doesn't work.  

EX,
mandra@ubuntu:/etc$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
 :-?[/QUOTE]
This is a highly unsual problem. Here's what, here is my sources list. Copy and paste it into your list by using the following process:
1. sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
2. sudo gedit /etc/apt/sources.list
3. delete everything that is in the file then copy and paste my sources list from below
4. save the file
5. sudo apt-get update
6. try to install j2re again

Sources list:


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Cheers,
GavinX

---

### Post by OttoDestruct on 2005-08-05
[Ubuntu Guide](http://ubuntuguide.org/) has this information and a crapload more. This alone has made my toying around with Ubuntu so much more time saving.

---

### Post by mandra on 2005-08-05
Success!!!   :) 

Thanks,  Must have been some hidden character or something like that.

It's working great now.

---

### Post by GavinX on 2005-08-05
[QUOTE=mandra]Success!!!   :) 

Thanks,  Must have been some hidden character or something like that.

It's working great now.[/QUOTE]
Which method did you use?

---

### Post by GavinX on 2005-08-05
[QUOTE=OttoDestruct][Ubuntu Guide](http://ubuntuguide.org/) has this information and a crapload more. This alone has made my toying around with Ubuntu so much more time saving.[/QUOTE]
Actually, he had followed the instructions in that guide to add the extra repositories. It's a matter that somewhere along the lines something went wrong and so had to be corrected. Good suggestion, nonetheless.

---

### Post by mandra on 2005-08-05
I was following the user guide but instead of using gedit I used VI to delete the hash marks that were commenting out the paths.  A wq! and I was set.  Or so I thought.

Just a note I put the text I copied from here into the file using VI and that worked fine.

Thanks again!

---

