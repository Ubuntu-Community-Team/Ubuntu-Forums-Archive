---
title: "Desktop background"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by nnjond on 2008-03-20
Hi,
I have decided I would like to have 3 Desks; 1,2, and 3. Can I fix it so I have diferent backgrounds so as to make  it clear which one I'm in?

Thanks.

---

### Post by StOoZ on 2008-03-20
you should check this out:
[http://ubuntuforums.org/showthread.php?t=69507&highlight=different+background+workspaces]("http://ubuntuforums.org/showthread.php?t=69507&highlight=different+background+workspaces")

---

### Post by nnjond on 2008-03-20
Thanks for your help. But I've got this far and now I'm stuck!

N.B. I have Ubuntu 7.10

nnjond@nnjond-desktop:~$ #!/bin/sh
nnjond@nnjond-desktop:~$ # Here are my notes from installing wallpapoz on Ubuntu Hoary Hedgehog 5.04. 
nnjond@nnjond-desktop:~$ # You can copy and save this and run it as a script.
nnjond@nnjond-desktop:~$ # The instructions are all here as comments.
nnjond@nnjond-desktop:~$ # I am an end-user and know not what I am doing. Use at your own risk
nnjond@nnjond-desktop:~$ # Good Luck! Tomy
nnjond@nnjond-desktop:~$ # STEP 1. Download two files:
nnjond@nnjond-desktop:~$ sudo wget -c [http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2](http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2)
[sudo] password for nnjond:
--18:50:57--  [http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2](http://wallpapoz.sf.net/temp/wallpapoz-0.2.tar.bz2)
           => `wallpapoz-0.2.tar.bz2'
Resolving wallpapoz.sf.net... 66.35.250.209
Connecting to wallpapoz.sf.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://wallpapoz.sourceforge.net/temp/wallpapoz-0.2.tar.bz2](http://wallpapoz.sourceforge.net/temp/wallpapoz-0.2.tar.bz2) [following]
--18:50:58--  [http://wallpapoz.sourceforge.net/temp/wallpapoz-0.2.tar.bz2](http://wallpapoz.sourceforge.net/temp/wallpapoz-0.2.tar.bz2)
           => `wallpapoz-0.2.tar.bz2'
Resolving wallpapoz.sourceforge.net... 66.35.250.209
Connecting to wallpapoz.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 41,941 (41K) [application/x-tar]

100%[====================================>] 41,941        26.50K/s             

18:51:00 (26.45 KB/s) - `wallpapoz-0.2.tar.bz2' saved [41941/41941]

nnjond@nnjond-desktop:~$ make
make: *** No targets specified and no makefile found. Stop.
nnjond@nnjond-desktop:~$ save as wallpapoz-install
The program 'save' is currently not installed.  You can install it by typing:
sudo apt-get install atfs
bash: save: command not found
nnjond@nnjond-desktop:~$ sudo apt-get install atfs
[sudo] password for nnjond:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libatfs1
The following NEW packages will be installed
  atfs libatfs1
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 277kB of archives.
After unpacking 737kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libatfs1 atfs
Install these packages without verification [y/N]? y
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe libatfs1 1.4pl6-9 [109kB]
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe atfs 1.4pl6-9 [168kB]
Fetched 277kB in 13s (20.1kB/s)                                                             
Selecting previously deselected package libatfs1.
(Reading database ... 109610 files and directories currently installed.)
Unpacking libatfs1 (from .../libatfs1_1.4pl6-9_i386.deb) ...
Selecting previously deselected package atfs.
Unpacking atfs (from .../atfs_1.4pl6-9_i386.deb) ...
Setting up libatfs1 (1.4pl6-9) ...
Setting up atfs (1.4pl6-9) ...
nnjond@nnjond-desktop:~$

---

### Post by Faud on 2008-03-20
What he typed in the code box were his instructions. Most of the time we use this so that people can copy and paste in terimnal...yes, but that is not the case this time.
You need to create a script for the install so open up gedit first and then copy and paste all of that in your new document, then save it and then make it excutibule(spelling). You can do that by right clicking on your saved file and checking the box that says "make excutibule(spelling again)" then double click the icon. But to be honest it doesn't look that bad you really shouldn't need a script. Just download it and compile it yourself.

---

### Post by Therion on 2008-03-20
Don't know if it's important to you or not but I'll mention it anyway.  If you install four different desktop wallpapers, you lose your desktop icons.  And unless something has changed, I don't mean "lose them" as in they disappear and you have to put them back, I mean you lose them forever.  You can't have four different desktop wallpapers AND desktop icons.  Period.  

As I recall, this has something to do with Nautilus, but I'm shaky on the details.

---

### Post by nnjond on 2008-03-20
Thanks again for all your help.

I have downloaded it successfully it seems- but am not sure of the compiling procedure?

Please can u help?

---

