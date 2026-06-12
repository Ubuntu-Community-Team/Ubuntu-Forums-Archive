---
title: "Build-essential problem with force"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by mahoodlum on 2006-07-23
Hi all, I posted this in another forum, but I am having trouble as a newbie to ubuntu and linux.  

I followed the instructions from here [http://www.ubuntuforums.org/showthread.php?t=209482&page=2](http://www.ubuntuforums.org/showthread.php?t=209482&page=2)

but I still get this

> $ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
build-essential: Depends: libc6-dev but it is not going to be installed or
libc-dev
Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages 



Currently Libc6 2.4 version is intalld
I tried to force the Libc6 3.4.6 version but it tells me a huge list of dependents will neeed to be removed I a fear removing most of them cause I am not sure how to backup my system or know if synaptic will still work.

---

### Post by catlett on 2006-07-23
In that post, the person had the wrong repositories for some reason. Change your repositories and try it again.
First make a copy of your repository list so you can undo what we are going to do just in case there is a problem.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
To reverse what we are going to do and get your original list back, do this command ```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list

``` Now we are going to give you a new list. This list comes from the daper guide [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
Enter this to open the list in a text editor 
```
sudo gedit /etc/apt/sources.list
``` Now erase everything in the page (don't worry we have a backup just in case) and enter this in it's place
> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-freeMake sure to hit SAVE at the top of gedit. Go back to the terminal and enter these commands 
```
sudo apt-get update
```
```
sudo apt-get install build-essential
```If you were having a repository issue like the other poster, this will take care of it.

---

### Post by mahoodlum on 2006-07-25
I am pretty sure it is not a repo problem, as the correct version is there, I need libc6 2.3.6 and that is there, however currently libc6 2.4 is installed, I can choice 2.3.6 and do a force, but the problem is there are other files that are dependent upon libc6 2.4.  Things like the following are forced to be unistalled if I force install libc6 2.3.6

pipenightdreams		deinstall
xserver-xorg		deinstall
agistudio		deinstall
snes9x-opengl		deinstall
libgnomecupsui1.0-1c2a		deinstall
aspell-en		deinstall
libopenexr2c2a		deinstall
mesa-utils		deinstall
pcsx-bin		deinstall
libwpd8c2a		deinstall
libarts1c2a		deinstall
libstdc++5		deinstall
libstdc++6		deinstall
amphetamine		deinstall
ekiga		deinstall
python2.4-gnome2-extras		deinstall
libglew1		deinstall
xserver-xorg-driver-v4l		deinstall
kdelibs4c2a		deinstall
python-opengl		deinstall
openoffice.org-gnome		deinstall
python2.4-apt		deinstall
xserver-xorg-driver-newport		deinstall

---

