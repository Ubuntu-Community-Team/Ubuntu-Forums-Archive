---
title: "howto : repair your broken ubuntu using livecd"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by AlexenderReez on 2007-04-25
firstly....the  **originally** howto can be found in tips and tutorials threat....i just forward this guide as i realized that this kind of guide doesn't exist in this section but it is really important . . . 
especially to those cases..
if you are running an upgrade and you forgot to connect your laptop to power supply then when synaptic doesn't  finish install software yet to your system...(after finished download)

or

your install software with command dpkg -i and that particular software doesn't have enough dependency then for sudden there will be broken software noticed by update manager ...for almost the time you can remove or reinstall it again using synaptic but how about when that particular broken installation broke your system and freeze your system

or

you shutdown your system and forgot that your software installation still running...

***for those all kind of situation or other situation that make you can't log on after restart even using 'safemode' ....so you need livecd to repair it...

put you livecd in and restart...then just lo on to livecd....

then open terminal

type

[QUOTE ]sudo mkdir /mnt/repair [/QUOTE]

> sudo mount /dev/?d?? /mnt/repair 

***noted** that ?d? mean part of your ubuntu root partition....it might be sda1...or hdb1 or sdb or whatever...depend where you install your ubuntu....

> sudo chroot /mnt/repair su 

> sudo apt-get update
sudo apt-get upgrade 
sudo  aptitude upgrade
sudo apt-get -f  install
sudo dpkg --configure -a
sudo apt-get upgrade


> exit
sudo reboot

take out your livecd...you should can run your ubuntu as usual .....:KS

---

### Post by gary4gar on 2007-04-25
wrong section!
reported

---

### Post by gigaferz on 2007-04-27
I updated my system, and I can only log in safe mode.

Id i try a normal session, the screen goes crazy, and then, brings me back to the log in screen, after 3 or 4 imes, it frteezes.

anybody there!, will this work?

---

### Post by outta_control on 2008-04-16
> **AlexenderReez said:**
> firstly....the  **originally** 


***noted** that ?d? mean part of your ubuntu root partition....it might be sda1...or hdb1 or sdb or whatever...depend where you install your ubuntu....


.:KS

You said that ?d? means part of your ubuntu root partition. How do I find out where that is? How do I find out where ubuntu is installed? Sorry I'm new at this.

---

### Post by Trail on 2008-04-17
For a minimally working system, type this:
```

cat /etc/fstab

```

You get an output like this:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
**# /dev/sda1**
UUID=0ad11260-eafc-40cb-a20d-4801bfdae453 **/**               ext2    defaults,errors=remount-ro 0       1
...

```

Search for the line that says that mountpoint is "/", and see the comment above it. This is what you are looking for.

---

### Post by Trail on 2008-04-17
And because I'm bored,

if you type the following in a terminal it _should_ show you which partition Ubuntu is mounted on.

```

cat /etc/fstab | grep -B1 -w '/' | head -n 1 | cut -c3-

```

---

### Post by DJ_Cripple on 2008-05-21
i have a broken ubuntu install after an attempt to upgrade from 6.06 to 8.04.  upgrade itself failed a couple of times, then eventually worked, now PC won't get past 'mounting root file system'
suspect it could be to do with firefox32/firefox64/icecat installs?

anyways, am attempting to follow these instructions. managed to figure out i am on sda2.

apt-get upgrades gives me errors about "unmet dependencies" 

[INDENT]The following packages have unmet dependencies:
  firefox-3.0: Depends: xulrunner-1.9 (>= 1.9~b5~) but it is not installed
               Depends: xulrunner-1.9 (< 1.9~b6~) but it is not installed
  xulrunner-1.9-gnome-support: Depends: xulrunner-1.9 (= 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1) but it is not installed
  yelp: Depends: xulrunner-1.9 but it is not installed[/INDENT]

and similar errors from aptitude upgrade

sudo apt-get -f install

gives me some errors about "perl: warning: Setting locale failed." and "/dev/pts not mounted?"
as well as another xulrunner error

will post full terminal output below.

any clues?  nautilus won't let me move those xulrunner files when running from the live cd... can i relatively safely delete them?

---

### Post by DJ_Cripple on 2008-05-21
Reading package lists... Done
root@ubuntu:/# sudo apt-get upgrade 
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  firefox-3.0: Depends: xulrunner-1.9 (>= 1.9~b5~) but it is not installed
               Depends: xulrunner-1.9 (< 1.9~b6~) but it is not installed
  xulrunner-1.9-gnome-support: Depends: xulrunner-1.9 (= 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1) but it is not installed
  yelp: Depends: xulrunner-1.9 but it is not installed
E: Unmet dependencies. Try using -f.
root@ubuntu:/# sudo aptitude upgrade
sudo: unable to resolve host ubuntu
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have unmet dependencies:
  firefox-3.0: Depends: xulrunner-1.9 (>= 1.9~b5~) but it is not installable
               Depends: xulrunner-1.9 (< 1.9~b6~) but it is not installable
  yelp: Depends: xulrunner-1.9 but it is not installable
  xulrunner-1.9-gnome-support: Depends: xulrunner-1.9 (= 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1) but it is not installable
root@ubuntu:/# sudo apt-get -f install
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xulrunner-1.9
The following NEW packages will be installed:
  xulrunner-1.9
0 upgraded, 1 newly installed, 0 to remove and 314 not upgraded.
995 not fully installed or removed.
Need to get 0B/8920kB of archives.
After this operation, 27.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "en_GB:en",
	LC_ALL = (unset),
	LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Can not write log, openpty() failed (/dev/pts not mounted?)
dpkg: regarding .../xulrunner-1.9_1.9~b5+nobinonly-0ubuntu4~8.04.0mt1_amd64.deb containing xulrunner-1.9:
 xulrunner-1.9 conflicts with j2re1.4
  j2re1.4 (version 1.4.2.02-1ubuntu3) is present and installed.
dpkg: error processing /var/cache/apt/archives/xulrunner-1.9_1.9~b5+nobinonly-0ubuntu4~8.04.0mt1_amd64.deb (--unpack):
 conflicting packages - not installing xulrunner-1.9
Errors were encountered while processing:
 /var/cache/apt/archives/xulrunner-1.9_1.9~b5+nobinonly-0ubuntu4~8.04.0mt1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# sudo aptitude safe-upgrade
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have unmet dependencies:
  firefox-3.0: Depends: xulrunner-1.9 (>= 1.9~b5~) but it is not installable
               Depends: xulrunner-1.9 (< 1.9~b6~) but it is not installable
  yelp: Depends: xulrunner-1.9 but it is not installable
  xulrunner-1.9-gnome-support: Depends: xulrunner-1.9 (= 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1) but it is not installable

---

