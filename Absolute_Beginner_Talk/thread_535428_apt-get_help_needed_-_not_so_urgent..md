---
title: "apt-get help needed - not so urgent."
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by detroit/zero on 2007-08-26
Alright, well, with some excellent help I managed to fix [a rather glorious snafu]("http://ubuntuforums.org/showthread.php?t=535026") I had going after I installed some automatic dependency-removing software.

I got my GUI back and managed to iron out a few kinks. I'm still having some problems, though, when I try to *apt-get install* any software I try to replace. I'm getting error messages from *dpkg,* and there seem to be a problem with *xcursor-themes* that I can't seem to fix.

It's a little lengthy, but here's a terminal output from trying to install a random package using apt-get, and what I'm doing subsequently:

```
zero@zero-laptop:~$ sudo apt-get install gparted
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcairomm-1.0-1 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a
The following NEW packages will be installed:
  gparted libcairomm-1.0-1 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1672kB of archives.
After unpacking 6316kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com feisty/main libcairomm-1.0-1 1.2.0-0ubuntu2 [42.7kB]
Get:2 http://us.archive.ubuntu.com feisty/main libglibmm-2.4-1c2a 2.13.3-0ubuntu1 [148kB]
Get:3 http://us.archive.ubuntu.com feisty/main libgtkmm-2.4-1c2a 1:2.10.8-0ubuntu1 [1156kB]
Get:4 http://us.archive.ubuntu.com feisty/main gparted 0.2.5-2ubuntu2 [324kB]                                                
Fetched 1672kB in 21s (78.2kB/s)                                                                                             
Selecting previously deselected package libcairomm-1.0-1.
(Reading database ... 113543 files and directories currently installed.)
Unpacking libcairomm-1.0-1 (from .../libcairomm-1.0-1_1.2.0-0ubuntu2_i386.deb) ...
Selecting previously deselected package libglibmm-2.4-1c2a.
Unpacking libglibmm-2.4-1c2a (from .../libglibmm-2.4-1c2a_2.13.3-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtkmm-2.4-1c2a.
Unpacking libgtkmm-2.4-1c2a (from .../libgtkmm-2.4-1c2a_1%3a2.10.8-0ubuntu1_i386.deb) ...
Selecting previously deselected package gparted.
Unpacking gparted (from .../gparted_0.2.5-2ubuntu2_i386.deb) ...
Setting up xcursor-themes (1.0.1-5ubuntu1) ...
update-alternatives: unable to make /usr/share/icons/default/index.theme.dpkg-tmp a symlink to /etc/alternatives/x-cursor-theme: No such file or directory
dpkg: error processing xcursor-themes (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libcairomm-1.0-1 (1.2.0-0ubuntu2) ...

Setting up libglibmm-2.4-1c2a (2.13.3-0ubuntu1) ...

Setting up libgtkmm-2.4-1c2a (2.10.8-0ubuntu1) ...

Setting up gparted (0.2.5-2ubuntu2) ...

Errors were encountered while processing:
 xcursor-themes
E: Sub-process /usr/bin/dpkg returned an error code (1)
zero@zero-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up xcursor-themes (1.0.1-5ubuntu1) ...
update-alternatives: unable to make /usr/share/icons/default/index.theme.dpkg-tmp a symlink to /etc/alternatives/x-cursor-theme: No such file or directory
dpkg: error processing xcursor-themes (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 xcursor-themes
E: Sub-process /usr/bin/dpkg returned an error code (1)
zero@zero-laptop:~$ sudo apt-get install xcursor-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xcursor-themes is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up xcursor-themes (1.0.1-5ubuntu1) ...
update-alternatives: unable to make /usr/share/icons/default/index.theme.dpkg-tmp a symlink to /etc/alternatives/x-cursor-theme: No such file or directory
dpkg: error processing xcursor-themes (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 xcursor-themes
E: Sub-process /usr/bin/dpkg returned an error code (1)
zero@zero-laptop:~$ sudo apt-get autoremove xcursor-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xcursor-themes
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 3940kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113581 files and directories currently installed.)
Removing xcursor-themes ...
update-alternatives: unable to make /usr/share/icons/default/index.theme.dpkg-tmp a symlink to /etc/alternatives/x-cursor-theme: No such file or directory
dpkg: error processing xcursor-themes (--remove):
 subprocess pre-removal script returned error exit status 2
update-alternatives: unable to make /usr/share/icons/default/index.theme.dpkg-tmp a symlink to /etc/alternatives/x-cursor-theme: No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 xcursor-themes
E: Sub-process /usr/bin/dpkg returned an error code (1)
zero@zero-laptop:~$ 

```

This happens with everything I'm reinstalling. Trying to remove/replace xcursor-themes just runs me in circles and gives me the two error codes.

I am running with a different set of cursor icons that I found on gnome-look.org, but I never deleted or did anything to the standard X mouse pointers; I just switched the defaults.

It did work fine before the mess I made in the above linked post, so I know it's not necessarily the mouse theme I'm currently using.

I'm up and running any real problems - even the errors shown in that terminal output aren't effecting the programs I'm replacing.I'm just bothered by the error message and can't seem to make it go away.

Thanks for any help.

---

### Post by detroit/zero on 2007-08-26
As a side note, I just noticed that along with my xcursor-themes being botched, I'm missing most of my fonts.

I have Neuropol set to be my titlebar font in Emerald, and it's even still listed as the font, but when I go to the select window, that one and probably 50 or so more are missing.

Anybody know if that particular one is part of a downloadable font package or if I can find it somewhere?

That should clear up all my stupid questions for now.

Thanks

---

### Post by detroit/zero on 2007-08-27
Here's another error messages. This one's a little different, I think - it's hard to keep track when you're seeing a million a day.

 Can anyone tell me what's going on here? I'm having some screwy stuff happening on my system - apps freezing randomly, sessions and settings not saving properly.. 

help?

```
zero@zero-laptop:~$ sudo apt-get autoremove mplayer
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mplayer-skins libmp4v2-0 libggi2 libgii1 libgii1-target-x liblame0 libfaac0
The following packages will be REMOVED:
  libfaac0 libggi2 libgii1 libgii1-target-x liblame0 libmp4v2-0 mplayer
  mplayer-skins
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 13.8MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 114324 files and directories currently installed.)
Removing mplayer ...
Removing libfaac0 ...
Removing libggi2 ...
Removing libgii1 ...
Removing libgii1-target-x ...
Removing liblame0 ...
Removing libmp4v2-0 ...
Removing mplayer-skins ...
Setting up xcursor-themes (1.0.1-5ubuntu1) ...
update-alternatives: unable to make /usr/share/icons/default/index.theme.dpkg-tmp a symlink to /etc/alternatives/x-cursor-theme: No such file or directory
dpkg: error processing xcursor-themes (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 xcursor-themes
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I go and look in */etc/alternatives,* *xcursor-themes* is there.
Doing an *apt-get install xcursor-themes* results in an error code as well.

---

