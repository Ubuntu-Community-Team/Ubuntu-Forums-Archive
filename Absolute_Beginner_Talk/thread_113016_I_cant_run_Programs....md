---
title: "I cant run Programs..."
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by Yautja_Ender on 2006-01-05
No matter what im doing it seems like if i dont install a program through synaptic i cant use it. I think from the messages i recieve i dont have the Administration rights to do anything... for example i input these lines of code into my console

Code:
```

```cd /opt/LimeWire/
./runLime.sh

Except you can subistitute frost wire in there cause im try to run it.... but it said that permission was denied.... what do i do?

---

### Post by equal on 2006-01-05
Well how are you installing it? We can't really tell what the problem is without knowing the issue.

Where are you downloading the program from? What is the exact name of the file you've downloaded? Let us know and we'll help you out!

---

### Post by Yautja_Ender on 2006-01-05
Ok, here is what i have downloaded and the directory its in: /home/ender/limewire-free_4.10.0-1_i386.deb

where do i go from here cause apparently the way i did it previously didnt work... i have java installed by the way....

---

### Post by Perfect Storm on 2006-01-05
Done this?

```

sudo dpkg -i /home/ender/limewire-free_4.10.0-1_i386.deb

```

---

### Post by Yautja_Ender on 2006-01-05
When i typed in that it said 
"dpkg: error processing /home/ender/limeiwre-free_4.10.0-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/ender/limeiwre-free_4.10.0-1_i386.deb"

---

### Post by Perfect Storm on 2006-01-05
Perhaps you should check for spelling errors ;)

---

### Post by Yautja_Ender on 2006-01-05
haha... good call
thanks... i think its up.... apparently it didnt work for frostwire cause i installed the java drivers after frostwire

---

### Post by Yautja_Ender on 2006-01-05
another question... sorry im such a newb but... how do i make it so i can install wma support to play movies...?

---

### Post by Perfect Storm on 2006-01-05
```
 sudo gedit /etc/apt/sources.list
```

Add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free[/b]

```
sudo apt-get update
sudo apt-get install w32codecs libdvdcss2 mplayer-586 mplayerplug-in

```

Though I also think you should try VLC (my favorite mediaplayer :D )

```

sudo apt-get install wxvlc

```

---

### Post by Yautja_Ender on 2006-01-05
hey id id what you said to get the codecs heres what it gave me back...:

ender@ubuntu:~$ sudo apt-get install w32codecs libdvdcss2 mplayer-586 mplayerplug-in
Password:
Reading package lists... Done
Building dependency tree... Done
Package mplayer-586 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer-586 has no installation candidate

---

### Post by Lord Illidan on 2006-01-05
Or use Amarok!!

---

### Post by Perfect Storm on 2006-01-05
[QUOTE=Yautja_Ender]hey id id what you said to get the codecs heres what it gave me back...:

ender@ubuntu:~$ sudo apt-get install w32codecs libdvdcss2 mplayer-586 mplayerplug-in
Password:
Reading package lists... Done
Building dependency tree... Done
Package mplayer-586 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer-586 has no installation candidate[/QUOTE]


Make sure to enable universe and multiverse in your sourcelist.

Or have a copy of mine: 

> 
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted
#deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe
#deb-src [http://dk.archive.ubuntu.com/ubuntu](http://dk.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
#deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
#deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Backports
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports-staging main universe multiverse restricted

#backports-extras
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main universe multiverse restricted

# Open Office 2 final
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

# Opera web browser
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free


---

### Post by hillbilly on 2006-01-05
[QUOTE=Yautja_Ender]hey id id what you said to get the codecs heres what it gave me back...:

ender@ubuntu:~$ sudo apt-get install w32codecs libdvdcss2 mplayer-586 mplayerplug-in
Password:
Reading package lists... Done
Building dependency tree... Done
Package mplayer-586 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer-586 has no installation candidate[/QUOTE]

```
sudo apt-get search mplayer
```

That should give you the name of the mplayer program that you can install.


Sorry the code should have been > sudo-cache search mplayer

---

