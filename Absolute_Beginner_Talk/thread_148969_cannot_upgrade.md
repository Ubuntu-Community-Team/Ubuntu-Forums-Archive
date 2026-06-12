---
title: "cannot upgrade"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by animesh on 2006-03-23
i first do 
sudo apt-get update

no problems ...

then i do
sudo apt-get upgrade and i get this
```
animesh@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  ttf-opensymbol wine
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 12.7MB of archives.
After unpacking 303kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  ttf-opensymbol wine
Install these packages without verification [y/N]? y
Get:1 http://wine.sourceforge.net binary/ wine 0.9.10~winehq1-2 [12.6MB]
Get:2 http://people.ubuntu.com ./ ttf-opensymbol 2.0.1-0breezy1 [151kB]
Err http://wine.sourceforge.net binary/ wine 0.9.10~winehq1-2
  Error reading from server. Remote end closed connection
Fetched 151kB in 1m36s (1570B/s)
Failed to fetch http://wine.sourceforge.net/apt/binary/wine_0.9.10~winehq1-2_i386.deb  Error reading from server. Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

hence i am unable to do
sudo apt-get dist-upgrade

---

### Post by animesh on 2006-03-24
please help in this i am unable to upgrade

---

### Post by int on 2006-03-24
You have some bad repository...


Use the ubuntu Repository...

---

### Post by meborc on 2006-03-24
ok... go to terminal and type:

**sudo gedit /etc/apt/sources.list**

gedit will open the file... delete all and replace with this: > #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 
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

save and close the file...

now type in terminal:

**sudo apt-get update**
and then 
**sudo apt-get upgrade**

---

### Post by animesh on 2006-03-24
will it work for ubuntu 5.04 Hoary ....??? becoz thts what i am using....

i already changed my sources list with the help of another good friend like you earlier and it looks like this

> deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

 deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./


And if there is some bad repo. why isn't it troubling me in update....??

---

### Post by animesh on 2006-03-29
please some body help.....
i cannot upgrade.....and hence can't do many things that require update

i have 5.04 Hoary

---

### Post by stoeptegel on 2006-03-29
Go here
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Put it on hoary, mark the sections you want and replace it with your own /etc/apt/sources.list file.

And do apt-get update & upgrade again.

The reason why your repo doesn't work might be due to some corrupt or missing files in the repo of wine, but i am unsure about that though.

---

### Post by IDipSkoalMint on 2006-03-29
This may be trivial, but have you tried using the GUI updater? ;)

---

### Post by animesh on 2006-03-31
you are talking about synaptic??? yes i have tried that and it also gives me error on upgrading...ie trying to reload

---

### Post by Princey on 2006-03-31
[QUOTE=animesh]you are talking about synaptic??? yes i have tried that and it also gives me error on upgrading...ie trying to reload[/QUOTE]

Something I do when I get problems trying to update is to manually type in the site address to see if it works. I'd suggest you check that repository as it seems to have a typo mistake as if you manually type the address in your browser you'll get a remote connection error. That seems to be the case as well when you run synaptic or apt-get update. Try commenting out this line:
> [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.10~winehq1-2 by placing # in front of it by running > sudo gedit /etc/apt/sources.list

Save and close gedit and try again. See if you get the same error message.

***Edit****
I just checked sourceomatic and there isn't a listed repository for hoary and Wine. Supported version listed was Breezy. I may be wrong, but you can check it out to be double sure.

---

### Post by jolger on 2006-03-31
try this

1.

if you know that your ipv6 is turned off skip this step

gedit /etc/modprobe.d/aliases

find the line
alias net-pf-10 pv6
replace with
alias net-pf-10 off #ipv6

save and close file...

2.
gedit /etc/apt/souces.list

replace "all" of it with
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

save and close file.

3.

if you skipped step 1 skip this one too

restart your computer (to make the changes in /etc/modprobe.d/aliases to take effect)

4.

apt-get update

5.

you should  be ready to go

---

