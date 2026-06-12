---
title: "apt-get dist-upgrade :-/"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2006-05-07
Hi,
today i upgraded my dist (don't know where to see what version i'm running though),
but some things couldn't be configured...

How do i (manually/automaticlly) configure them?

This is the output i get
```
Fouten gevonden tijdens behandelen van:
initramfs-tools
evms
evms-ncurses
linux-image-2.6.15-21-386
hal
linux-image-386
hwdb-client
gnome-volume-manager
update-notifier
mdadm
hal-device-manager
linux-restricted-modules-386
linux-386
lvm-commom
lvm2
```

Please note that i am a complete noob in linux ;) 


Iarwain

---

### Post by Kimm on 2006-05-07
Just try installing one of them (apt-get install evms, for example), then you can see why it wount install, then try to install the package that it depends on, untill it agrees to remove some old package in favor of the new one (dependecy issues).

Just be carefull with what you remove.

---

### Post by Iarwain ben-adar on 2006-05-07
thanks for the reply :D

anyways, installing one by one doesn't work either :s

```
<<snip>>

dpkg: vereistenproblemen verhinderen de configuratie van update-notifier:
 update-notifier is afhankelijk van hal; maar:
  Pakket hal is nog niet geconfigureerd.
dpkg: fout bij afhandelen van update-notifier (--configure):
 vereistenproblemen - blijft ongeconfigureerd
Fouten gevonden tijdens behandelen van:
 initramfs-tools
 udev
 mdadm
 lvm-common
 lvm2
 evms
 evms-ncurses
 hal
 gnome-volume-manager
 hal-device-manager
 hwdb-client
 linux-image-2.6.15-21-386
 linux-image-386
 linux-restricted-modules-2.6.15-21-386
 linux-restricted-modules-386
 linux-386
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

(if you can't read dutch => )> dpkg: dependencies withold configuring update-notifier:
update-notifier is dependant of hal; but: 
Packet hal is not yet configured.
dpkg: error whilst treating (?) update-notifier (--configure):
dependency problem - stays unconfigured


Iarwain

---

### Post by gingermark on 2006-05-07
Please post the contents of your sources.list file (located in /etc/apt)

---

### Post by Iarwain ben-adar on 2006-05-07
> # Specialized Basic Ubuntu Multimedia Preparation Script sources.

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ dapper main restricted

## Uncomment the following two lines to fetch updated software from the network

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

## Seveas' Repo's
deb [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) breezy-seveas all
deb-src [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) breezy-seveas all


deb [http://issaris.be/breezy](http://issaris.be/breezy) ./



Iarwain

---

### Post by Iarwain ben-adar on 2006-05-08
Nobody knows something?

Anyways, after i rebooted my machine, it was totally at a loss :(

hal wouldn't start nomore, so now i have no internet, no music, no extra hard drives...

How can i rescue my system?


Iarwain

---

### Post by Gustav on 2006-05-08
You should remove these lines:```
## Seveas' Repo's
deb http://users.lichtsnel.nl/~seveas breezy-seveas all
deb-src http://users.lichtsnel.nl/~seveas breezy-seveas all


deb http://issaris.be/breezy ./
```from your /etc/apt/sources.list (since they are for breezy and you are running dapper) and then run```
sudo apt-get update
sudo apt-get dist-upgrade
```
If that doesn't work you can try to run```
sudo dpkg-reconfigure <package>
``` for all packages that needs to be configured

---

### Post by Iarwain ben-adar on 2006-05-08
can't do,
because i don't have no internet :-/

my "hal" is not working...


Iarwain

---

### Post by Gustav on 2006-05-08
try typing:```
sudo dpkg-reconfigure <package-name>
```for your unconfigured packages. (I don't know if it will work, but maybe :))

---

### Post by Iarwain ben-adar on 2006-05-08
Will try it asap (not at linux-pc atm)

Thanks for the reply :-)


Iarwain

---

### Post by az on 2006-05-08
Run

sudo dpkg --configure -a

and then

sudo apt-get -f install

---

### Post by Iarwain ben-adar on 2006-05-08
the "--configure -a" command gives me the same output :s

But i tried a bit further, and i saw that it needed kernel 2.6.12 (and i have 2.6.12.x)

don't really get it :s
Even when i start up, i can chose between 3 different kernels (i believe 2.6.12.x, 2.6.10-6 and 2.6.10-5)

=> .x gives me the kernel error (strange me thinks) (NOTE: with this kernel, i can't start gdm. My core devices couldn't be loaded: /dev/input/mice is not found. /dev/input doesn't even exist on the .x kernel. It does on the .10-5)
=> .10-6 won't boot (kernel panic or something similar)
=> .10-5 boots, but no hal (and other programs as well)


Iarwain

---

### Post by Iarwain ben-adar on 2006-05-09
bumpie x 2


Iarwain

---

### Post by Iarwain ben-adar on 2006-05-09
No one can help me further?

Do i just reinstall Ubuntu?


Iarwain

---

