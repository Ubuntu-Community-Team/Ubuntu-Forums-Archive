---
title: "Adobe flash not installing"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by revelationman on 2008-01-01
This is very frustrating  I got the wireless working and just one small bs thing
sorry to dampen peoples parade on Linux but if Linux wants to take off and challenge Microsoft oneday it must deal with the stupid things like this or else it will just get frustrated users 

I have tried everything downloaded the tar file followed the instructions to the letter and still get same bs answer 


brian@brian-laptop:~$ tar xvfz install_flash_player_9_linux.tar.gz
tar: install_flash_player_9_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
brian@brian-laptop:~$ 

The file and directory is there just this system is being a pain in the *** 

Sadly  most web sites use flash so  really  if this does not work we must wait till this bug is corrected 

Again it is small assine issues like this that makes Redmond laugh and rub their hands 

So  any  suggestions 

Just a frustrated new user

---

### Post by BL00dFox on 2008-01-01
Maybe this will help::

[http://ubuntuforums.org/showthread.php?t=655226](http://ubuntuforums.org/showthread.php?t=655226)

---

### Post by hyper_ch on 2008-01-01
Flash installation is currently bugged. You need to manually install it from teh tar.gz file:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by kestrel1 on 2008-01-01
Had the same problem, but got it sorted.
All I did was un-tar the Flash files to a folder on the desktop. CD to the folder from a terminal eg. cd Desktop/Flash_folder or whatever you name the folder. Then just run this command:
sudo ./flashplayer-installer

Hope it works for you.

---

### Post by frenchsquared on 2008-01-01
how do I un tar the folder

---

### Post by kestrel1 on 2008-01-01
To un-tar the file you can just double click on it & select Extract on the program that opens up.

---

### Post by Myglaren on 2008-01-01
> **frenchsquared said:**
> how do I un tar the folder
Right click and select "extract here"
Damn, too slow with the post button

---

### Post by alienexplorers on 2008-01-01
Try in terminal:
> tar -xvzf Name.tar.gz

---

### Post by frenchsquared on 2008-01-01
gordon@Asus:~/Desktop/flash$ sudo ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

gordon@Asus:~/Desktop/flash$

---

### Post by Myglaren on 2008-01-01
You will need to get Gnash for a 64 bit system until the bugs are ironed out.
It works but isn't 100%

---

### Post by frenchsquared on 2008-01-01
im trying to uninstall Gnash, it is horible at least the version I have
my site are all giberish

so does that mean Im running a 64bit system?

---

### Post by frenchsquared on 2008-01-01
Ok so i got flash installed
but I guess I installed the 32bit or something
beacuse when I got to a flash site (ljcfeed.com)
it says i need to install missing plugins, when I
try to install them it says they are already installed.

This Sucks

Im a flash designer(student) I have to have flash
Would have been nice for the school to tell us flash doesnt work for linux users

---

