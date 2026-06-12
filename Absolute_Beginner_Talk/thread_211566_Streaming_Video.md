---
title: "Streaming Video"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-07-08
I was trying to watch the World Cup video highlights in Ubuntu (Dapper), but it won't work. Here is the link:
[http://fifaworldcup.yahoo.com/06/en/v/](http://fifaworldcup.yahoo.com/06/en/v/)

When I try to watch any video from this website, a window opens up which then stops after a while. And there is nothing on the screen. I have seen many threads regarding problems of watching streaming video on Ubuntu, but I could not really figure out what the solution was. 

Any help would be appreciated.

---

### Post by DSn0wMan on 2006-07-08
I was able to slove this problem by installing easy ubuntu. It's a nice little gui script that will help you get things like streaming video working with a few simple clicks.

Here is a list of the things it can do

[http://easyubuntu.freecontrib.org/overview.html](http://easyubuntu.freecontrib.org/overview.html)

---

### Post by catlett on 2006-07-08
You need mplayer. But you have to enable extra repositories to get it.These are the commands to install ```
sudo apt-get install mplayer
```
```
sudo apt-get install mozilla-mplayer
``` If you do not have extra repositories enabled the easiest thing is to just copy my list.
First do this command to create a backup ```
sudo cp /etc/apt/sources.list /etc/apt/aources.list_backup
``` Then open your list in a text editor ```
sudo gedit /etc/apt/sources.list
``` Noe erase everything on the page and replace it with this
> # 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free Now issue this command and then repeat the earlier comands
```
sudo apt-get update
``` Just for good measure let's install basic mp3 playback and get you window's codecs
```
 sudo apt-get install mpg321 vorbis-tools
```
```
 wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
```
  ```
sudo dpkg -i w32codecs_20060611-0.0_i386.deb 
``` and java and flash just in case you don't have them
```
 sudo apt-get install flashplugin-nonfree 
```
```
 sudo update-flashplugin 
```
```
 sudo apt-get install sun-java5-jre sun-java5-plugin 
```

---

### Post by aam-aadmi on 2006-07-08
I had the extra repositories; so I just went ahead and installed MPlayer. But, I still cannot see the video highlights from the FIFA website. Might be a problem with the format of the video files?

---

### Post by blackjack6.21.91 on 2006-07-08
> sudo apt-get install mozilla-mplayer
wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)
sudo dpkg -i w32codecs_20060611-0.0_i386.deb
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin 

I would do those things as well.  Just in case.  If that doesn't work install easyubuntu.  It should resolve everything.

---

