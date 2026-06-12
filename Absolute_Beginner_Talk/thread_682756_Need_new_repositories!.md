---
title: "Need new repositories!"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by jesusfreak107 on 2008-01-30
Ack! I apparently messed up my repositories somehow! I can't get updates for almost anything, and I can't find a whole bunch of packages that other people say they get out of their package manager.  Could someone in the US kindly copy/paste the entire contents of their 7.10 Gutsy Gibbon Sources.list file? I seem to be having a problem adding/removing them, too. could someone give me a quick tutorial? I thought I knew, but apparently not.  Also, if anyone knows of any other major repositories that have a ton of cool packages in them, feel free to share!
:guitar:

---

### Post by bumanie on 2008-01-30
First back up your present list. 
> sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup then
> gksudo gedit /etc/apt/sources.list
Clear the text in the geidt box and replace with this
> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced 
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main 

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free 

Obtained from here
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by LowSky on 2008-01-30
in terminal what does it say if you try to run the following 
```
 sudo apt-get update
```

What programs are you looking to install that you can't? got these instuctions from psycocats 
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

You might need to turn on some options, First, go to System > Administration > Software Sources
A dialogue will appear that shows you which repositories are currently enabled. The ones with the checked (or ticked) boxes are enabled. The others are not enabled. 

Check (or tick) the unchecked (or unticked) boxes. You may also want to choose to use a local server instead of the main server. I chose Server for United States, since I live in the United States. You may also want to uncheck (or untick) the CD-ROM/DVD source. Otherwise, every time you try to install software, you may be prompted to insert the Ubuntu installer disc. If you have a working internet connection, you will want to use the online servers for software installation. Once you do this, you'll be asked to reload the repository information. This allows Ubuntu to see what software is newly available to you. Click Reload to continue. 

Then, wait for the information to be reloaded. Once that's done, the window will disappear, and you'll be able to use apt-get, Synaptic, or Add/Remove to install new programs. More information about software installation can be found here. 

also add medibuntu repos follow these instructions (for gutsy only) (cut and paste in terminal)

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
add dvd playback
```
sudo apt-get install libdvdcss2
```.

add codecs (music/movie formats)
```
sudo apt-get install w32codecs
```

---

### Post by jesusfreak107 on 2008-01-30
THANK YOU VERY MUCH, LOWSKY AND BUMANIE i AM INSTALLING MY 36TH UPDATE NOW, AFTER USING BOTH OF YOUR SOLUTIONS!i ALSO NOW HAVE OVER 2000 MORE PACKAGES IN MY SYNAPTIC PACKAGE MANAGER! I GAVE YOU ALL A BIG THANK YOU!
:popcorn::popcorn::popcorn::popcorn::popcorn:

---

