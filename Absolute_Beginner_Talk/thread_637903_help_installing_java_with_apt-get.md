---
title: "help installing java with apt-get"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by DFord425 on 2007-12-11
can anyone tell me tell me the name of the package i would need for java 6 SE?

---

### Post by PeterJS on 2007-12-11
sun-java6-bin

FYI: The package is in the multiverse repository.

---

### Post by jken146 on 2007-12-11
The JRE (runtime environment) is sun-java6-bin
The JDK (development kit) is sun-java6-jdk

They are in multiverse.

---

### Post by DFord425 on 2007-12-11
I tried those and its not working, it says```
E: Couldn't find package sun-jdk-6u3-linux-i586.bin
```

---

### Post by FuturePilot on 2007-12-11
Try this
```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts
```

---

### Post by jken146 on 2007-12-11
Do you have all the repositories enabled (System > Admin > Software Sources)?  Are you using 64bit Ubuntu?

---

### Post by umattu on 2007-12-11
Why don't you use add/remove to install java?

make sure that "all available packages" is selected in the upper right hand corner, search java, and installation is a few clicks away.

---

### Post by DFord425 on 2007-12-11
I tried using the add/remove, but it gave me an error saying it conflicts with other installed software.

---

### Post by DFord425 on 2007-12-11
I tried this ```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin sun-java6-fonts
```
and it started to work but then i got this message
```
E: Broken packages
```

---

### Post by FuturePilot on 2007-12-11
Try
```
sudo apt-get install -f
```
This will attempt to fix any broken packages.

---

### Post by DFord425 on 2007-12-11
I use the -f switch with apt-get and i still get broken packages.  When i get the error i get a message before it saying ```
The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (= 6-03-0ubuntu2) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-03-0ubuntu2) but it is not installable

```
what does that mean?

---

### Post by FuturePilot on 2007-12-11
Seems like something might be wrong with your sources.list. 
Can you post the output of
```
cat /etc/apt/sources.list
```

---

### Post by DFord425 on 2007-12-11
here is what i get when i run ```
cat /etc/apt/sources.list
```
```
dford@dford-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse universe
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by FuturePilot on 2007-12-11
Ah, almost all your sources are commented out. So you're going to need to uncomment them
```
gksudo gedit /etc/apt/sources.list
```
Remove the "#" sign from every line that begins with deb and deb-src
Then save it and run
```
sudo apt-get update
```
Then try running the command for Java I posted earlier.

---

### Post by R_T_H on 2007-12-13
I have the same problem (not able to install Java), and, like Dford425, I have the entries in the source list commented out in just the same way. However, typing "gksudo gedit /etc/apt/sources.list" does not open anything - it enters fine, but nothing appears to occur. I tried it with sudo instead, but the terminal said "sudo: gedit: command not found".

Could you tell me what I'm doing wrong please?

---

### Post by FuturePilot on 2007-12-13
> **R_T_H said:**
> I have the same problem (not able to install Java), and, like Dford425, I have the entries in the source list commented out in just the same way. However, typing "gksudo gedit /etc/apt/sources.list" does not open anything - it enters fine, but nothing appears to occur. I tried it with sudo instead, but the terminal said "sudo: gedit: command not found".

Could you tell me what I'm doing wrong please?

Are you using Gnome or another desktop environment?

---

### Post by R_T_H on 2007-12-13
Xfce - I use Xubuntu. I've found out what was wrong about using "sudo gkedit" etc., i.e. that mixing gui codes with terminal codes doesn't work. I don't really know what to do, so I think I'll install it again while connected to the internet. Therefore, the installer will be able to verify it and the lines of stuff won't be commented out.

---

### Post by oldos2er on 2007-12-13
You don't need to reinstall, just fix your sources.list. Try 'sudo nano /etc/apt.sources.list' in a terminal.

---

### Post by R_T_H on 2007-12-14
Thanks people. I've solved the problems due to commenting out, and this evening after school I'll find out if it has worked.

For the record, after experimenting around, I can tell you that commands including "gedit" will probably not work on Ubuntu variants (i.e. they'll only work on Ubuntu Prime). This is because (I think) gedit is a gnome application, whereas Xubuntu comes with "mousepad", an equivalent text editor. I changed the command to "sudo mousepad /etc/apt/sources.list". 

Thanks for your time

---

### Post by GSF1200S on 2007-12-14
> **R_T_H said:**
> Thanks people. I've solved the problems due to commenting out, and this evening after school I'll find out if it has worked.

For the record, after experimenting around, I can tell you that commands including "gedit" will probably not work on Ubuntu variants (i.e. they'll only work on Ubuntu Prime). This is because (I think) gedit is a gnome application, whereas Xubuntu comes with "mousepad", an equivalent text editor. I changed the command to "sudo mousepad /etc/apt/sources.list". 

Thanks for your time

You are absolutely correct. For XFCE its mousepad, for Gnome its gedit, and for KDE its kate or kwrite. Nano can always be used, whether it be in a terminal or at the actual command line.

And once you edit your sources.list, be sure to do a 

```
sudo apt-get update
```

and then a 

```
sudo apt-get upgrade
```

This will update apt, and then bring your machine to an updated state. After that, Java should be easy to install as said above. Good Luck ;)

---

### Post by R_T_H on 2007-12-15
I typed in sudo apt-get update and the terminal had this to say:

E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

?

EDIT: Though I have no clue as to the reason why it came up with the above message. However, it installed like a charm when I tentatively tried using Synaptics. Thanks people!

---

### Post by Perfect Storm on 2007-12-15
Properly when you tried running the update command you had synaptic or add/remove open. Make sure to close those or vice versa.

---

