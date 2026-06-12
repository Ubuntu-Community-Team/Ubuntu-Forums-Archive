---
title: "Now that I passed on my CD, I now need it to install gcc and g++."
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by chcarver on 2008-03-18
I gave my Ubuntu CD away after installing it to another in need of Ubuntu. But now it looks like I'll always need the CD if I'm to install certain packages.

I need to install gcc and g++, but I can't as it's asking for the CD. Is there a way to gather this from the internet?

$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libartsc0 kdelibs-data liblualib50 liblua50 libaudio2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc
  manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3940kB/7935kB of archives.
After unpacking 31.9MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

$

---

### Post by taurus on 2008-03-18
Actually, you don't need to use the installer CD anymore.  Gedit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save the changes and close down gedit window.

Now run

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by bodhi.zazen on 2008-03-18
Remove the CD from you sources.

```
gksu gedit /etc/apt/sources.lst
```

Put a # in front of the line with the CD (at the very top)

Remove a # from the sectio for universe / multiverse

Save and exit gedit.

```
sudo apt-get update && sudo apt-get install build-essential && apt-get autoremove
```

---

### Post by which_chick on 2008-03-18
I got this from the documentation on repositories :  [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Under the section "Managing local repositories" it says this:

If you would like Synaptic to rely solely on the internet repositories for package management, you can disable the CD-ROM entry with a few steps:

1.  Launch Synaptic and navigate to "Settings" > "Repositories".
     
 A list of software repositories or "Channels" will be shown.

2.   Locate the entry for the CD-ROM (it may say something like CD disk with Ubuntu 6.06 LTS). Click on the checkbox next to it to disable the CD-ROM as a software source.

3.  Click the Close button to save the changes you have made.
    
NOTE:  You can re-enable the CD-ROM at any time using the checkbox next to its entry.

(These directions say that they are for Edgy and Dapper but they will probably still work for Gutsy.  The menus and stuff are the same, just as described in these directions, so it's worth a try.)

Hope that this helps.

---

