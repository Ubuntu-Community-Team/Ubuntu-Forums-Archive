---
title: "Useful tips for newbies goes here"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by daredevil on 2006-02-24
hi all.. i used to note down all my findings.. here r some. most of them may be from kubuntu and ubuntu forums but they r not consolidated. a must hav for newbies... sorry for some repeating posts. hope its useful.. ill keep updating new findings in this topic. ur comments r welcome

Mounting Windows Partitions in Ubuntu
------------------------------------------------------

```
http://www.psychocats.net/linux/mountwindows.php
```


linux beginers
------------------------------
```

http://www.linuxcommand.org/
http://www.ubuntuforums.org/showthread.php?t=73885&highlight=command-line+beginners
http://linuxreviews.org/beginner/#toc1

```

setting PATH and JAVA_HOME variables
-------------------------------------------------------------
```

open: VI /etc/profile and add :
#path variable for java
export JAVA_HOME=/usr/local/java/jdk1.5.0_04
export PATH=$JAVA_HOME/bin:$PATH

```

apt-get tutorials
-------------------------
```

http://newbiedoc.sourceforge.net/system/apt-get-intro.html

```

kubuntu 5.10 breezy
-----------------------
```
http://ftp.ecc.u-tokyo.ac.jp/UBUNTU-CDS/kubuntu/5.10/kubuntu-5.10-install-i386.iso

```
install flash player
-----------------------
```
http://kubuntu101.blogspot.com/2005/11/installing-macromedia-flash-player.html

```
install wine
-------------------------
```
http://kubuntu101.blogspot.com/2005/10/installing-wine.html
```

install kubuntu step by step
--------------------------------
```
http://whoiam55.at.preempted.net/?p=18
```

debian commands
-----------------
```
http://www.debianhelp.co.uk/pkgadm.htm
```

install firefox
-------------------
```
https://wiki.ubuntu.com/FirefoxNewVersion

http://ubuntuforums.org/showthread.php?t=105343

```

Alt-F2
Code:
konsole
Once the Konsole opens up:
Code:
sudo apt-get update
sudo apt-get install firefox

install realplayer
--------------------
```
http://kubuntuforums.net/forums/index.php?topic=2882.0

```
install software in ubuntu
-----------------------------
```
http://www.psychocats.net/linux/installingsoftware.php
```

checking disk space
-----------------------
```
df -h will give you a human view (with GB, MB, and KB)
```

checking your ip address
--------------------------------------
```
ifconfig
```

windows to linux
------------------
```
http://www.linuxrsp.ru/win-lin-soft/table-eng.html
```

bittorrent
----------------------
```
azereus
```

firewall
----------------
```
firestarter
```

IDE Ot
--------------
```
kdevelop

http://www.ogre3d.org/wiki/index.php/Kubuntu_Install_here
```

to build essential packages
-------------------------------------------
```
sudo apt-get install build-essential

```
automatix
unrar

changing host name
------------------------------
```
sudo vi /etc/hosts
```

install vlc
-----------------
```
first, edit your sources.list by:
Code:
sudo kwrite /etc/apt/sources.list
and uncomment (fancy word for removing the # signs) the lines starting with deb. It should now look like:
Code:
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu breezy universe
deb-src http://ca.archive.ubuntu.com/ubuntu breezy universe
Now, run
Code:
sudo apt-get update
and
Code:
sudo apt-get install vlc
Now, if you want a better looking front-end (not that the default is ugly, but some people are impressionate)
Code:
sudo apt-get install qvlc

```
install avg and yahoo messenger
-------------------------------------------------
```
you will need to install either python-gtk2 or python-gtk-1.2, most likely the first one for AVG. python-gtk-1.2 is in the universe repository, so that will need to be enabled in your /etc/apt/sources.list.

as for ymessenger, you need to install libgtk1.2 (also in universe) but installing python-gtk-1.2 should automatically install this as it is a dependency.

yahoo is using the older gtk version 1.2 for the UI, which is kinda clunky. ymessenger usually works fine, but imo most people end up migrating to kopete or gaim for stability and features.

```
changing host name
------------------------------
```
http://www.cpqlinux.com/hostname.html
```

wine and media player repository
-------------------------------------------------
```
First of all use WINE from wineHq not the one in the ubuntu repository.

Add this to your sources.list:
deb http://wine.sourceforge.net/apt/ binary/

Then install wine.

I would also recomend installing IE6 and Windows Media player with the Sidenet Configuration Utility, which can be found at:

http://sidenet.ddo.jp/winetips/config.html

It will give you a good start at getting a correctly setup fake windows directory.

```
test wine
--------------
```
$ cd /windows (or whereever the Windows drive is)
$ cd WINDOWS (or possibly WINNT)
$ wine notepad.exe
```

repositories
-------------------------
```
deb http://kubuntu.org/packages/kde35 breezy main
deb ftp://mirror.mcs.anl.gov/pub/ubuntu breezy main restricted
deb ftp://ubuntu.mirrors.tds.net/ubuntu breezy universe
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://kubuntu.org/packages/kde35 breezy main
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb ftp://ubuntu.mirrors.tds.net/ubuntu breezy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-security main restricted universe
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-updates main restricted

deb-src ftp://mirror.mcs.anl.gov/pub/ubuntu breezy main restricted
deb-src ftp://ubuntu.mirrors.tds.net/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src ftp://ubuntu.mirrors.tds.net/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb-src ftp://mirror.mcs.anl.gov/pub/ubuntu breezy-updates main restricted
```

other repositories and ubuntu starter guide
--------------------------------------------------------------
```
http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories

```
root sudo
----------------
```
https://wiki.ubuntu.com/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d

$ sudo <command>
is the same as
# <command>

```

create new user
--------------------------
```
kdesu systemsettings
sudo useradd -m -p <password> <login>
```

quick restart
--------------------
```
For quicker rebooting, press ctrl + alt + backspace. This stops the X server. To start it back up, type startx. Just thought I'd throw that in there to speed up your troubleshooting process...

```
reconfigure xserver
----------------------------
```
sudo dpkg-reconfigure xserver-xorg

```
install automatix
-----------------------------
```
sudo apt-get remove automatix-kubuntu
sudo apt-get install xterm libglade2-0 libgnomecanvas2-0
wget http://kambing.vlsm.org/ubuntu/pool/main/z/zenity/zenity_2.10.0-0ubuntu1_i386.deb
sudo dpkg -i zenity_2.10.0-0ubuntu1_i386.deb
wget http://beerorkid.com/automatix/automatix_5.0-2_i386.deb
sudo dpkg -i automatix_5.0-2_i386.deb

Please note: To remove softwares installed by automatix, visit the following thread:
http://ubuntuforums.org/showthread.php?t=90797

To uninstall Automatix, do the following from terminal:
Code:

sudo apt-get remove automatix
```

sources.list generator
---------------------------------
```
http://www.ubuntulinux.nl/source-o-matic
```

video codecs
--------------------
```
sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8
```

install and run azureus
----------------------------------
```
http://ubuntuforums.org/showthread.php?t=75272

```
linux file system guide
-------------------------------
```
http://www.neowin.net/forum/index.php?showtopic=260796
```

install netbeans
------------------------
```
https://wiki.ubuntu.com/Netbeans4%2e1onAMD64
```

reinstall grub / lilo
--------------------------
```
sudo apt-get remove grub --purge
sudo apt-get install grub

```
install mplayer
------------------------
```
https://wiki.ubuntu.com/MplayerInstallHowto

```
about codecs
---------------------
```
https://wiki.ubuntu.com/RestrictedFormats#head-848295cba1b3591a4b4a0dbea5844fd5d2894b6b

```
help
--------
```
https://wiki.ubuntu.com/HowToGetHelp
http://help.ubuntu.com/
https://wiki.ubuntu.com/UserDocumentation
https://wiki.ubuntu.com/
http://users.bigpond.net.au/hermanzone/

```
install mySQL
-----------------------
```
https://wiki.ubuntu.com/MYSQL5FromSource

```
shortcuts
----------------
```
press ctrl + alt + esc to get a skull icon and use it to click on any application u want to terminate

press ctrl + esc to open kde sys guard to list all the running process. u can also terminate unwanted processes

```
sites
----------
```
http://www.tinyapps.org/internet.html
http://www.freedownloadscenter.com/
```

linux sites
--------------
```
http://linuxcommand.org/learning_the_shell.php
http://www.ss64.com/bash/
```

hope this continues
cheers
Sriram

---

### Post by WebScud on 2006-02-24
I tried upgrading Firefox via:

```
sudo apt-get update
sudo apt-get install firefox
```

And I got a message that said I had the latest version of Firefox installed (which was 1.0.7).  I thought oh, maybe I made a mistake and had 1.5.0.1 installed, so I tried to run Firefox and the app wouldn't boot.  I just get the busy mouse icon and then nothing happens.

---

### Post by bixin on 2006-02-24
Just a tip:  Something not working as expected? Research it, and as you look through and try suggestions WRITE DOWN EACH STEP YOU TRIED. This has helped me alot in figuring out Ubuntu, I've written steps down only to look back and say dang i forgot to do this or i typed it wrong. It helps, then again I am forgetful. 

Don't get to frustrated just take a break from it for a few minutes. Alot of things require your root password. Good cause it makes you think before you go "rooting":D  around and tinkering, tedious when you just want to do something simple as in delete a file. Sometimes your laptop led light for you wifi connection will work, sometimes it will work only when you got a connection, or when its doing something or sometimes its constantly on. I guess it depends on manufactures.

I came to Unbuntu cold, as in I had no freaking clue what a terminal was and where it was located, and I am still learning. Through all my hair pulling sessions( took me 2 days to get my wifi connection going with live cd when i first started) I can honestly say, I still like Ubuntu, I like the problem solving aspect(although it has ended), the feel of it and the idea and passion behind it.

---

### Post by daredevil on 2006-02-26
To graphically view the currently running processes press

ctrl + esc

To view the currently running processes press from console type the following at console

ps -el

---

### Post by RaiSuli on 2006-02-26
@ WebScud: To my knowledge the Firefox version in the repositories is not 1.5, but 1.07. So you would need to update Firefox either manually from the Firefox site or use Automatix to install it for you.

---

### Post by mjfleck2000 on 2006-02-26
>>sudo apt-get update
>>sudo apt-get install firefox

apt-get update will find all new programs that can be installed.
apt-get install firefox will INSTALL firefox on your comuter.  You probably already have firefox installed.  If you want to UPGRADE an installed program, I would suggest:

apt-get update
apt-get upgrade

If there are new versions of programs, the above command will fetch and install them for you.  And, as RaiSuli noted, version 1.5.0.1 is not in the Breezy repositories, so apt-get upgrade would NOT upgrade to 1.5.0.1

Mike

---

### Post by daredevil on 2006-02-26
WebScud i think u must refer to this article to install the latest version of firefox ie 1.5  i tried it and it works great....

install firefox
-------------------
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by daredevil on 2006-03-01
JRE for firefox

```
http://www.debian-administration.org/articles/142
```

---

