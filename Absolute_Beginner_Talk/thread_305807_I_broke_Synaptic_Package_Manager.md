---
title: "I broke Synaptic Package Manager"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by DanFromWinterpeg on 2006-11-23
Hi,

I am a tech support geek who knows his way around nearly any version of Windows ever created, but when it comes to any flavor of Linux this is my very first attempt at running any distro and I am already running into problems.  I am running Dapper and I seem to have broken my Synaptic Package Manager.  I can no longer download and install ANYTHING.  I can get online just fine, but now every time I try and download and install updates or install packages I get the following errors.  Does anyone have a clue as to what the heck I did?  About the only thing I changed recently that I can think of is I setup encryption on my wireless network.

Any help would be greatly appreciated.](*,) [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.13.11ubuntu7_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.13.11ubuntu7_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.2_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by scrooge_74 on 2006-11-23
spooky, it seems synaptic is looking ay your own machine for the repos.

What did you do?

Check your source file is ok sudo gedit /etc/apt/sources.list

Edit:
My source.list looks like this which is the basic config


# deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://pa.archive.ubuntu.com/ubuntu/](http://pa.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by David Corrales on 2006-11-23
Remove the anonimity proxy.

---

### Post by scrooge_74 on 2006-11-23
Lei una vez sobre ese proxy, pero nunca lo instalé

---

### Post by rlozano on 2006-11-24
do you have an internet connection? and is your IP address pointing to the right direction? it seems that you are just looping in your machine.

---

### Post by David Corrales on 2006-11-24
> **scrooge_74 said:**
> Lei una vez sobre ese proxy, pero nunca lo instalé

Yo vi un post hace unos días con el mismo problema y era que tenían habilitado ese proxy. Supongo que hace un loopback y luego salen los paquetes pero como que a Synaptic no le gusta mucho lol.

---

