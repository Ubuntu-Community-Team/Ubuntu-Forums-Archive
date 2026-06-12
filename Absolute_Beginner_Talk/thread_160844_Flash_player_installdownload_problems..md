---
title: "Flash player install/download problems."
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by BLZPLZ on 2006-04-15
Whenever I try to download Macromedia Flash player, regardless of the source, be it download.com, macromedia.com etc. it just freezes up time and time again.  It's kind of getting in the way of my web surfing ability.](*,)  Any suggestions?

---

### Post by aysiu on 2006-04-15
Try [this](http://www.ubuntuforums.org/showpost.php?p=924125&postcount=2) (forget about the first command... unless, of course, you downloaded the .tar.gz from Macromedia).

---

### Post by BLZPLZ on 2006-04-15
see...my problem is that the install file itself won't download, let alone install.  

I think that link you directed me to is for if you already have the install file downloaded..??:-?

---

### Post by BLZPLZ on 2006-04-15
matt@Champagne:~/Desktop$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: The package bmp-docklet needs to be reinstalled, but I can't find an archive for it.

I followed that tutorial regardless, and that was the error message i got.  Any clues as to what is happening?

---

### Post by aysiu on 2006-04-15
bmp-docklet?

That's weird. I don't believe *flashplugin-nonfree* is in any way related to *bmp-docklet*.

Do you have [the right repositories enabled](http://www.psychocats.net/ubuntu/sources)? Did you do a ```
sudo apt-get update
``` before trying to install Flash?

---

### Post by esteban2x on 2006-04-15
I tried the apt-get method but it said:
E: Couldn't find package flashplugin-nonfree

any ideas out there?

---

### Post by BLZPLZ on 2006-04-15
i enabled the right repositories *and* did the sudo apt-get update command right after.  I'm confused.

---

### Post by aysiu on 2006-04-16
[QUOTE=BLZPLZ]i enabled the right repositories *and* did the sudo apt-get update command right after.  I'm confused.[/QUOTE] Well, just to double-check, can you post the output of all of these commands? Yes, the entire output *and* what you typed. ```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by BLZPLZ on 2006-04-16
matt@Champagne:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
matt@Champagne:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [45.6kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [38.4kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [14.4kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [31.7kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.5kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Fetched 279kB in 4s (65.8kB/s)
Reading package lists... Done
matt@Champagne:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: The package bmp-docklet needs to be reinstalled, but I can't find an archive for it.
matt@Champagne:~$

---

### Post by htinn on 2006-04-16
For Dapper/Hoary, you install "flashplugin-nonfree". For Breezy you need to install "flashplayer-mozilla".

---

### Post by aysiu on 2006-04-16
That's weird. Apparently, [there's no such thing as *bmp-docklet*.](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=bmp-dockl&searchon=name&subword=1&version=all&release=all)

Did you install Beep Media Player from source (.tar.gz), by chance?

Hm.

Maybe you can try ```
sudo apt-get -f install
```

---

### Post by BLZPLZ on 2006-04-21
I never use beep media player, would uninstalling it solve the problem?  
If so, how do I go about doing that?

---

### Post by luopio on 2006-04-22
[EDIT] nevermind.. the servers came back up I did the install the manual way and got sound to work by editing /etc/firefox/firefoxrc. can't believe sounds were disabled by default... [/EDIT]

so any ideas on where to get the flash-package? The macromedia server seems to be down and I can't find any mirrors. The problem is that the deb also tries to download the package there and hangs like this: 

Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 124620 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_7.0.63.1-ubuntu1_i386.deb) ...
Setting up flashplugin-nonfree (7.0.63.1-ubuntu1) ...

---

### Post by onx on 2006-04-22
[QUOTE=luopio]so any ideas on where to get the flash-package? The macromedia server seems to be down and I can't find any mirrors. [/QUOTE]

Same problem here mate, I really hope Adobe gets that all sorted out.

---

