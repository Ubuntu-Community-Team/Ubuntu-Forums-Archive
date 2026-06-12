---
title: "Flubox Package?"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by joh@n on 2006-03-24
Hi,

I recently installed Ubuntu, and I am attempting to install Fluxbox ](*,) , however on the Fluxbox download page there are distributions for some linux distros but not ubuntu! :-k 

Which of these would be more appropriate for Ubuntu?
[LIST]
[*]Debian Package
[*]Fedora Package
[*]Suse Package
[*]FreeBSD Package
[/LIST]

Also, is KDE required to run Fluxbox, or is Fluxbox stand-alone?

Thanks in advance.

Johan.

---

### Post by wsanders on 2006-03-24
Ubuntu is a Debian fork, so the Debian package should work. Not sure about KDE, though.

---

### Post by Sef on 2006-03-24
> Also, is KDE required to run Fluxbox, or is Fluxbox stand-alone?

Fluxbox is a stand alone window manager.  You don't need any other window manager to run it.

> I recently installed Ubuntu, and I am attempting to install Fluxbox  , however on the Fluxbox download page there are distributions for some linux distros but not ubuntu! 

To install fluxbox, read this wiki on Ubuntu:

[https://wiki.ubuntu.com/Fluxbox?highlight=%28Fluxbox%29]("https://wiki.ubuntu.com/Fluxbox?highlight=%28Fluxbox%29")

---

### Post by joh@n on 2006-03-24
[QUOTE=wsanders]Ubuntu is a Debian fork, so the Debian package should work. Not sure about KDE, though.[/QUOTE]

Ok, I will give the Debian package a go. I guess I will find out whether KDE is required or not regardless. 

Thanks!

---

### Post by Sef on 2006-03-24
> Ok, I will give the Debian package a go. I guess I will find out whether KDE is required or not regardless. 

Be sure and **back up** your home files first, in case, the Debian package breaks your software.  Ubuntu is based on Debian, but the packages are not necessarily interchangeable.

Any way, see my first post (two posts up.)

---

### Post by joh@n on 2006-03-24
[QUOTE=Sef]Be sure and **back up** your home files first, in case, the Debian package breaks your software.  Ubuntu is based on Debian, but the packages are not necessarily interchangeable.[/QUOTE]

Ok, I have downloaded a fully compatible copy of Fluxbox that was apparently designed for ubuntu, which I presume is good.
I have backed up my home files regardless (as sef kindly suggested).
However I have hit another issue.
I have a .deb package, however it fails to un-archive and throws the following error at  me.

Could Not Open "FileName"!
Archive Type Not Supported...

Is there some other basic procedure I am missing here to install this window manager?

Thanks for the help everyone.

---

### Post by wsanders on 2006-03-24
How are you trying to unarchive? The best way is usuallly through the terminal.
```

sudo dpkg -i [package name]

```

---

### Post by Sef on 2006-03-24
Joh@n:

the wiki link  to install fluxbox on Ubuntu is up now.  Here it is again.

[https://wiki.ubuntu.com/Fluxbox?highlight=%28Fluxbox%29]("https://wiki.ubuntu.com/Fluxbox?highlight=%28Fluxbox%29")

This will work fine.

---

### Post by taurus on 2006-03-24
Tell me again why do you have to download .deb for fluxbox when you can install it with apt-get???  I am not sure exactly what you want to do here!!!  :rolleyes:

---

### Post by joh@n on 2006-03-24
[QUOTE=wsanders]How are you trying to unarchive? The best way is usuallly through the terminal.
```

sudo dpkg -i [package name]

```[/QUOTE]

Right, thanks for that, getting there. Unfortunatley another disaster has occured.
Could somebody please advise, as this is jibberish to me!

> jheath@primidius:~$ sudo dpkg -i /home/jheath/Desktop/fluxbox_0.9.14-1_i386.deb Selecting previously deselected package fluxbox.
(Reading database ... 56661 files and directories currently installed.)
Unpacking fluxbox (from .../fluxbox_0.9.14-1_i386.deb) ...
Adding `diversion of /usr/bin/bsetroot to /usr/bin/bsetroot.blackbox by fluxbox'Adding `diversion of /usr/share/man/man1/bsetroot.1.gz to /usr/share/man/man1/bsetroot.blackbox.1.gz by fluxbox'
dpkg: dependency problems prevent configuration of fluxbox:
 fluxbox depends on menu (>= 2.1.19); however:
  Package menu is not installed.
 fluxbox depends on libimlib2; however:
  Package libimlib2 is not installed.
dpkg: error processing fluxbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fluxbox


Thanks once again!

---

### Post by joh@n on 2006-03-24
Sef thanks for the Wiki,

Taurus, Im fairly new to the Ubuntu OS, hence that is my I am posting in the Absolute Beginners Talk, please dont expect me to know how to use apt-get or even what it is! Perhaps you could tell me?

Thanks!

---

### Post by taurus on 2006-03-24
```

sudo apt-get install fluxbox

```
After reboot, click Session from the GUI login screen and choose fluxbox as your window manager...

---

### Post by joh@n on 2006-03-24
[QUOTE=taurus]```

sudo apt-get install fluxbox

```
After reboot, click Session from the GUI login screen and choose fluxbox as your window manager...[/QUOTE]

Ummm, hit yet another problem, I can only sudo that package if I uncomment the the universe lines in /etc/apt/sources.list. Problem is I can't un-comment those lines, the file is read only and the only user who can edit the file is apparently root.
There is no root account on a default Ubuntu installation right?

---

### Post by Sef on 2006-03-24
To enable sources, follow this link:

[http://ubuntuforums.org/showthread.php?t=146315&highlight=%2Fetc%2Fapt]("http://ubuntuforums.org/showthread.php?t=146315&highlight=%2Fetc%2Fapt")

---

### Post by joh@n on 2006-03-24
[QUOTE=Sef]To enable sources, follow this link:

[http://ubuntuforums.org/showthread.php?t=146315&highlight=%2Fetc%2Fapt]("http://ubuntuforums.org/showthread.php?t=146315&highlight=%2Fetc%2Fapt")[/QUOTE]


Thanks Sef, you are really good with these link things. ;)

---

### Post by Sef on 2006-03-24
Your welcome.  Glad I could help you.

---

