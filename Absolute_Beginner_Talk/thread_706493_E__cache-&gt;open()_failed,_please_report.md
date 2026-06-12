---
title: "E: _cache-&gt;open() failed, please report"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by pmasterp on 2008-02-24
When I try to run synaptic this is what I Got:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Then when I run 'sudo dpkg --configure -a' I got the following information:

danipab@danipab-desktop:~$ sudo dpkg --configure -aSetting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

dpkg: dependency problems prevent configuration of avant-window-navigator:
 avant-window-navigator depends on libawn0 (>= 0.2.1); however:
  Package libawn0 is not installed.
dpkg: error processing avant-window-navigator (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of awn-manager:
 awn-manager depends on avant-window-navigator (>= 0.2); however:
  Package avant-window-navigator is not configured yet.
dpkg: error processing awn-manager (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1

Also I try to get the deb packages of libwan0 but I got the same message to run 'dpkg --configure -a'

Please Help

---

### Post by deepclutch on 2008-02-24
firstly,u have got a wrong(read "#"ed) /etc/apt/sources.list OR u did not do 
"sudo apt-get update" often with internet connected.
if u have done so, a "sudo apt-get install -f" would have solved the problem.
For now,u download libawn0 from below page for 32-bit(i386) or 64-bit(amd64) depending on ur distro .
[U][http://packages.ubuntu.com/gutsy-backports/libs/libawn0](http://packages.ubuntu.com/gutsy-backports/libs/libawn0)

see ^ the backport distro?
[/U] 
install libawn0_xx.deb ad "dpkg -i /to/pathofdeb/libawn0_xx.deb



now regarding ur kernel initram related error,it seems that the distro is messed up(may be env variables?)
do as below when internet is connected.
```
sudo apt-get install --reinstall util-linux 
```u may like to do the same to initramfs-tools
as:
```
sudo apt-get install --reinstall initramfs-tools
```and make sure ur /etc/apt/sources.list is as below:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

# Medibuntu - Ubuntu 7.10 "gutsy gibbon"
# GPG key-file: http://packages.medibuntu.org/medibuntu-key.gpg
deb http://packages.medibuntu.org/ gutsy free non-free
# deb-src http://packages.medibuntu.org/ gutsy free non-free

# Seveas&#8217; packages (GPG key: 1135D466)
# GPG key-file: http://mirror.ubuntulinux.nl/1135D466.gpg
deb http://mirror.ubuntulinux.nl gutsy-seveas all
# deb-src http://mirror.ubuntulinux.nl gutsy-seveas all

deb http://ppa.launchpad.net/mozillateam/ubuntu gutsy main


```U can edit  ur /etc/apt/sources.list by GUI text editor as below(incase u panic with terminal :p )
press **ALT+F2** to get a run dialog,inside run below command:
```
gksudo gedit /etc/apt/sources.list 
```look my gutsy xorg.conf for reference and correct.then run "sudo apt-get update && sudo apt-get upgrade [/code]
when a prompt come for giving password,give ur user's password for authentification;that's it! 

and [http://ubuntuguide.org](http://ubuntuguide.org) will be helpful may be for you :) happy Linuxing !

---

### Post by pmasterp on 2008-02-24
I do everything, but no mather what I do I got the same message: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

and I did that and got the same previous message also synaptic has broken packages and don't know how to fix it!

---

### Post by deepclutch on 2008-02-24
^aah!dont say that!We all experience such pkg deps and errors more often :p esp in distros like Debian Sid which I use ;)
try!download the libawn0 from the link I gave .then install it as
"sudo dpkg -i libawn0_version..deb "

I think u should follow the lines slowly to try.

I can gurantee 99.999% that if u had followed the solutions I gave,the problem will be already solved :p

---

### Post by pmasterp on 2008-02-25
> **deepclutch said:**
> ^aah!dont say that!We all experience such pkg deps and errors more often :p esp in distros like Debian Sid which I use ;)
try!download the libawn0 from the link I gave .then install it as
"sudo dpkg -i libawn0_version..deb "

I think u should follow the lines slowly to try.

I can gurantee 99.999% that if u had followed the solutions I gave,the problem will be already solved :p

deepclutch you're amazing just did sudo dkpg -i (packagename).deb and voila ubuntu went back to normal you rock thanks.

---

