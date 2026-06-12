---
title: "Installing OpenVPN - Configuring and 'make' problems"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Calculator on 2006-09-12
I am installing OpenVPN onto my server running Ubuntu 6.06 (newly installed) which requires the following steps:

	./configure
	make
	make install

However, when I type the 'make' instruction I get the following in my terminal window:

root@Server1:/home/Stuff/lzo-2.02# make
make: *** No targets specified and no makefile found.  Stop.
root@Server1:/home/Stuff/lzo-2.02# cd /home/Stuff/openvpn-2.1_beta15/

What is the target?

How do I specify a 'target' using a make command?

Thanks

---

### Post by Najand on 2006-09-12
Do you have "build-essential" installed?
If not try:
```

sudo apt-get install build-essential

```

---

### Post by Calculator on 2006-09-12
Thanks Najand

Problem is that I do not have my install CD available:

Typing in the command: 
 sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  g++ g++-4.0 libstdc++6-4.0-dev
Suggested packages:
  gcc-4.0-doc lib64stdc++6 libstdc++6-4.0-doc stl-manual
The following NEW packages will be installed:
  build-essential g++ g++-4.0 libstdc++6-4.0-dev
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3750kB of archives.
After unpacking 14.3MB of additional disk space will be used.
[B]Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)'
in the drive '/cdrom/' and press enter[/B]

Can I get the 'build-essential' from the net?

Thanks

---

### Post by Calculator on 2006-09-13
I have installed 'Build essential' however, my "Make" requires a target - can someone please give me some insight into this issue.  Thanks


root@Server1:/home/michael/Michaels_Stuff/lzo-2.02# sudo apt-get install 
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  g++ g++-4.0 libstdc++6-4.0-dev
Suggested packages:
  gcc-4.0-doc lib64stdc++6 libstdc++6-4.0-doc stl-manual
The following NEW packages will be installed:
  build-essential g++ g++-4.0 libstdc++6-4.0-dev
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3750kB of archives.
After unpacking 14.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libstdc++6-4.0-dev.
(Reading database ... 195236 files and directories currently installed.)
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.3-1ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.0.3-1_i386.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up g++-4.0 (4.0.3-1ubuntu5) ...
Setting up libstdc++6-4.0-dev (4.0.3-1ubuntu5) ...

Setting up g++ (4.0.3-1) ...

Setting up build-essential (11.1) ...
root@Server1:/home/michael/Michaels_Stuff/lzo-2.02# make
make: *** No targets specified and no makefile found.  Stop.
root@Server1:/home/michael/Michaels_Stuff/lzo-2.02#

---

### Post by Calculator on 2006-09-13
Fixed - I found that I have to run all the commands in sequence.  Not just the one that I got stuck on.

:)

---

### Post by JohnW on 2006-09-22
Why are you compiling from source?  Openvpn is in the repositories.  Not sure which one, I'd already gone into Synaptic Settings|Repositories and unchecked CD, checked all others offered, but it's there somewhere.

---

### Post by steve.horsley on 2006-09-22
> **JohnW said:**
> Why are you compiling from source?  Openvpn is in the repositories.  Not sure which one, I'd already gone into Synaptic Settings|Repositories and unchecked CD, checked all others offered, but it's there somewhere.

I'll second that. It's Soo much easier.

---

### Post by josh34 on 2006-10-15
Could someone provide step-by-step instructions for installing openvpn-2.1 on a fresh ubuntu install? Here is the download link: [http://openvpn.net/download.html](http://openvpn.net/download.html) and I have to use version 2.1_beta16 and compile using lzo compression.

---

### Post by capn_hector on 2006-10-15
> **JohnW said:**
> Why are you compiling from source?  Openvpn is in the repositories.  Not sure which one, I'd already gone into Synaptic Settings|Repositories and unchecked CD, checked all others offered, but it's there somewhere.

compiling from source gives greater control over options and its more configurable.  plus once you can compile from source, you can install programs on any linux distro.

---

### Post by Avian00 on 2006-11-28
> **JohnW said:**
> Why are you compiling from source?  Openvpn is in the repositories.  Not sure which one, I'd already gone into Synaptic Settings|Repositories and unchecked CD, checked all others offered, but it's there somewhere.

I'll tell you why *I* wouldn't install OpenVPN from Repos...   The version in the Dapper Repos is 2.0.6, a known-buggy version of OpenVPN (configured by the release notes of 2.0.7).  If they'd update this package in the Repos, I might consider using them.  Otherwise, I'm forced to install from source on this one.  Oh well.

---

### Post by gallafent on 2007-10-15
> **Avian00 said:**
> I'll tell you why *I* wouldn't install OpenVPN from Repos...   The version in the Dapper Repos is 2.0.6, a known-buggy version of OpenVPN (configured by the release notes of 2.0.7).  If they'd update this package in the Repos, I might consider using them.  Otherwise, I'm forced to install from source on this one.  Oh well.

Why? Looking at the OpenVPN changelog at [http://openvpn.net/changelog.html](http://openvpn.net/changelog.html), I do not see any changes between 2.0.6 and 2.0.9 (current) which affect the Linux version. All the changes since 2.0.6 have apparently been to do with the Windows version. What bugs are you aware of in 2.0.6 which affect the Linux version?

---

### Post by PacketCollision on 2007-10-15
If you really want to compile the latest version, install prevu ([https://wiki.ubuntu.com/Prevu](https://wiki.ubuntu.com/Prevu)) and compile a backport from edgy, feisty or gutsy.  Prevu makes deb packages, and handles depencencies, but lets you have a newer version.

---

