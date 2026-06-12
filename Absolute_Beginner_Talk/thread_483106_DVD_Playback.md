---
title: "DVD Playback"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by chrisbish on 2007-06-24
I can't get a dvd to play.
i tried to follow the tutorial here [http://ubuntuforums.org/showthread.php?t=413624]("http://ubuntuforums.org/showthread.php?t=413624")

but it hasn't worked out

once i typed in the comand to open up the list of sources it came up in read only mode and i can't edit or save it.

---

### Post by mattg89 on 2007-06-24
Sounds like you didn't put "sudo" or "gksudo" in front of the commads

---

### Post by chrisbish on 2007-06-24
i have maganed to get it to come up now by using the root terminal

but when i use the > wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add - comand it come up with

> root@chris-desktop:/home/chris# wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
gpg: no valid OpenPGP data found.
root@chris-desktop:/home/chris# 


---

### Post by Ayuthia on 2007-06-24
Try using:
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

You will also need to update the repositories. Instead of:
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free 

It should be:
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

---

### Post by chrisbish on 2007-06-24
first bit:
> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

root@chris-desktop:/home/chris# wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
OK
root@chris-desktop:/home/chris# 



second bit:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

is the second bit right?

---

### Post by chrisbish on 2007-06-24
its working now

thanks

---

### Post by erick_tuk on 2007-07-07
Hi, I'm new to Linux (6 months now) I want to stop using windows xp, find Ubuntu much better for me. Here's my problem, I can't playback DVDs, it says: are you trying to play an encrypted dvd without libdvdcss? But I have libdvdcss, libdvdcss2, and most repositories I've read about in forums, the last time I had Ubuntu I could play them, but not every DVD, I believe blockbuster has some kind of a lock, help would be very much appreciated.

Erick

---

### Post by RomeReactor on 2007-07-07
Hi. Did you follow the steps described in this thread? If so, then you most likely still have **totem-gstreamer**, which is a little problematic for DVDs, in my opinion. You need to change it to **totem-xine**:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```
after that, DVDs should play. Also, you must have done this previously (after you installed **libdvdcss**):
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by euler_fan on 2007-07-07
I prefer VLC for my media needs. It is powerful and works. Once, before I understood the libdvdcss thing it actually played a DVD--scrambled. Then I installed it properly and it works great!

---

