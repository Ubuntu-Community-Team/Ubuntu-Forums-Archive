---
title: "Failed Driver Removal Prohibits the Modification of any Packages"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by radiocognition on 2008-01-15
Hey Everyone,

I was recently trying to get my video card (Radeon 9200) to work and I've run into a bit of trouble.  In my long and extensive search to fix my graphics card, I heard of a program called Envy that automatically installs proprietary drivers for the card.  After installing the program, I tried to remove the old ATI driver (fglrx) and install the proprietary driver instead.  The script marked fglrx for removal but failed to remove the driver (it appears if Ubuntu itself would not let me remove the driver).  I gave up on the video card again for a while, but I noticed that any new packages I had marked for installation or upgrade always failed as apt-get was also trying to remove the marked fglrx package.  Here is the code from when I try to autoremove from apt-get:

```

true@true-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 51 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 45.2MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 108835 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/etc/xdg/compiz/compiz-manager' with
  different file `/etc/xdg/compiz/compiz-manager.ubuntu', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I was able to install critical updates by using the dselect command, I cant figure out how to unmark the removal of fglrx.  Synaptic package manager is unable to deselect the removal of the package (I click the unmark box and nothing happens).  Im running out of ideas.  Suggestions?

---

### Post by mikeyphi on 2008-01-15
> **radiocognition said:**
> Hey Everyone,
 Here is the code from when I try to autoremove from apt-get:

```

Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/etc/xdg/compiz/compiz-manager' with
  different file `/etc/xdg/compiz/compiz-manager.ubuntu', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):

```
 Suggestions?

If you are still getting the above error re overwriting a file - try the following:
Open a terminal - then
make a backup copy of '/etc/xdg/compiz/compiz-manager' 
then enter the following code;
sudo dpkg -i --force-overwrite (/etc/xdg/compiz/compiz-manager)
sudo apt-get -f install

If that doesn't work properly - just put the backup file copy back in place.

---

### Post by radiocognition on 2008-01-15
Didnt work.  Here is the relevant output:
```

true@true-desktop:~$ sudo cp /etc/xdg/compiz/compiz-manager /etc/xdg/compiz/compiz-manager.backup
[sudo] password for true:
true@true-desktop:~$ cd /etc/xdg/compiz
true@true-desktop:/etc/xdg/compiz$ ls
compiz-manager  compiz-manager.backup  compiz-manager.ubuntu
true@true-desktop:/etc/xdg/compiz$ cd

true@true-desktop:~$ sudo dpkg -i --force overwrite /etc/xdg/compiz/compiz-manager
dpkg-deb: `/etc/xdg/compiz/compiz-manager' is not a debian format archive
dpkg: error processing /etc/xdg/compiz/compiz-manager (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /etc/xdg/compiz/compiz-manager

true@true-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 60 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 45.2MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 108835 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/etc/xdg/compiz/compiz-manager' with
  different file `/etc/xdg/compiz/compiz-manager.ubuntu', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by mikeyphi on 2008-01-15
> **radiocognition said:**
> Didnt work.  Here is the relevant output:
```

true@true-desktop:~$ sudo dpkg -i --force overwrite /etc/xdg/compiz/compiz-manager

```

Check there wasn't a typo! Should be "force-overwrite"

You may also want to try:
Make a backup copy of /etc/xdg/compiz/compiz-manager
delete the original file
try install again!

Again if it doesn't work - rename your backup to it's original status.

Addition:...just noticed - you already have a file called /etc/xdg/compiz/compiz-manager.ubuntu

---

### Post by mikeyphi on 2008-01-15
Would the reinstallation of the driver be the answer?
If the driver doesn't cause you any problems - you could reinstall xorg-driver-fglrx

---

### Post by radiocognition on 2008-01-15
I tried to see if a typo was the problem - I got the same error message.  I would have reinstalled the driver but I an unable to mark the driver for re instillation and or unmark the driver for removal from synaptic.

---

### Post by mikeyphi on 2008-01-15
Last suggestion - before I get into the books!
Open a terminal and enter:
sudo dpkg --configure -a

---

### Post by radiocognition on 2008-01-15
I tried sudo dpkg --configure -a and its still not working.  I've been looking through the MAN for apt-get to see if there is a way to deselect packages.  This is really getting frustrating for me.  I am unable to install from any of Ubuntu's repositories

---

