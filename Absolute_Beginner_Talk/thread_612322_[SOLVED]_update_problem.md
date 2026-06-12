---
title: "[SOLVED] update problem"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by skyjacker on 2007-11-13
Anyone know what is going on here? Two times today I got notified that there were upgrades to be installed. When I installed them I got this error BOTH times.  Help please.:confused:

"There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."

---

### Post by taurus on 2007-11-13
Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by skyjacker on 2007-11-14
> **taurus said:**
> Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```Here is update

:Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US

Here is upgrade:
skyjacker@skyjacker-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  libpoppler-qt2 libpoppler2 poppler-utils
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 854kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libpoppler2 0.6-0ubuntu2.1 [662kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main libpoppler-qt2 0.6-0ubuntu2.1 [72.5kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main poppler-utils 0.6-0ubuntu2.1 [120kB]
Fetched 854kB in 2s (313kB/s)
(Reading database ... 98385 files and directories currently installed.)
Preparing to replace libpoppler2 0.6-0ubuntu2 (using .../libpoppler2_0.6-0ubuntu2.1_i386.deb) ...
Unpacking replacement libpoppler2 ...
Preparing to replace libpoppler-qt2 0.6-0ubuntu2 (using .../libpoppler-qt2_0.6-0ubuntu2.1_i386.deb) ...
Unpacking replacement libpoppler-qt2 ...
Preparing to replace poppler-utils 0.6-0ubuntu2 (using .../poppler-utils_0.6-0ubuntu2.1_i386.deb) ...
Unpacking replacement poppler-utils ...
Setting up libqt3-mt (3:3.3.8really3.3.7-0ubuntu11.1) ...

Configuration file `/etc/qt3/qt_plugins_3.3rc'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** qt_plugins_3.3rc (Y/I/N/O/D/Z) [default=N] ?     What do i do about this???

---

### Post by Partyboi2 on 2007-11-14
Check software sources list (System-Admin-software sources)
make sure 'installable from cd-rom/dvd is unticked
:)

---

### Post by skyjacker on 2007-11-14
> **Partyboi2 said:**
> Check software sources list (System-Admin-software sources)
make sure 'installable from cd-rom/dvd is unticked
:)I have kubuntu - where is (System-Admin-software sources) in it?:confused:

---

### Post by Partyboi2 on 2007-11-14
Sorry, I thought you were using ubuntu. I should have read the post more carefully:rolleyes:

---

### Post by chiefbearclaw on 2007-11-14
```
sudo gedit /etc/apt/sources.list
```

Or substitute gedit with whatever program your using.. for example.. in LinuxMint (which uses mousepad)

```
sudo mousepad /etc/apt/sources.list
```

This will open up the sources.list (which Synaptic Package Manager uses when updating or getting software) and let you modify it since you are using root with the sudo command. :)

---

### Post by joao82 on 2007-11-15
this qt_plugins_3.3rc configuration file also gave me problems after an update. after that I couldn't open Adept Manager because it kept telling me the process was already in use.
I could only solve this when I went to the terminal and installed a program through apt-get (htop for example). then it asked me what to do about qt_plugins_3.3rc and I just told it to install the new one.

---

