---
title: "Setting up the Kubuntu 6.06 CD as a repository"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by mozza314 on 2006-08-03
Hi, I have just re-installed ubuntu and want to set up a Kubuntu CD as a repository to install the Kubuntu-Desktop package (to have an Ubuntu/Kubuntu cohabitation).

I open Synaptic, uncheck all the normal repositories and add the Kubuntu CD. When I go back to the list of packages (and reload the list), the Kubuntu-Desktop package is not there. In fact, none of the familiar Kubuntu packages are there, particularly amaroK which I want to install.

In the list of packages, some of those not installed are:
avm-fritz-firmware
avm-fritz-firmware-2.6.15-23
binutils
bpalogin
build-essential
capiutils
cpp
cpp-4.0
dpkg-dev
drdsl


and these appear when the cd is checked as a repository (as opposed to no repositories checked), even when the cd is out when reloading the list!

I also have an edubuntu cd and have managed to find the edubuntu-desktop package, unfortunately I am not interested in it, but it's very confusing to me that the edubuntu cd works but not the kubuntu cd.


 - Very confused, please help.

---

### Post by ciscosurfer on 2006-08-03
Go [here to create a sources.list]("http://www.ubuntulinux.nl/source-o-matic") that you can use.  Read about it first, then copy your current sources.list so you can revert if need be.  Be sure to set your proper system name (breezy, dapper, etc.) and the country code if you wish.

First save/copy your current sources.list```
cd /etc/apt
sudo cp sources.list sources.list_backup
sudo gedit sources.list
```and modify your list with the new one that you create at source-o-matic.

---

