---
title: "[SOLVED] Today's auto updates broke open office dependencies -"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-05
Sorry this a repost but original title not explaining real problem
sudo dpkg --configure -a
Password:
Setting up ttf-opensymbol (2.2.0-1ubuntu5) ...
Updating fontconfig cache...
/usr/share/fonts/truetype: failed to write cache
/usr/share/fonts/truetype/msttcorefonts: failed to write cache
etc etc

[http://ubuntuforums.org/showthread.php?t=567803](http://ubuntuforums.org/showthread.php?t=567803)

---

### Post by useResa on 2007-10-05
I just (5 minutes ago) did today's upgrade using the terminal and did not encounter the issue you have indicated.
FYI I update using the following command:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by philinux on 2007-10-05
What does that terminal command do

---

### Post by philinux on 2007-10-05
Same errors I'm afraid

---

### Post by philinux on 2007-10-05
This happened before in April. Something about touching directories. Beyond me but seems like a bug.

---

### Post by philinux on 2007-10-06
anyone?

---

### Post by J11Gyro on 2007-10-06
Had the same problem yesterday and am still trying to sort it out.

---

### Post by philinux on 2007-10-06
found this from April [http://ubuntuforums.org/showpost.php?p=2401087&postcount=4](http://ubuntuforums.org/showpost.php?p=2401087&postcount=4)

Also there has been a bug reported for gutsy same thing. Anyway I tried this touch thing with the list of fonts and I now get this but wiithout the list of fonts cache erros as before

Setting up ttf-opensymbol (2.2.0-1ubuntu5) ...
Updating fontconfig cache...
/usr/share/fonts/truetype/msttcorefonts: failed to write cache
dpkg: error processing ttf-opensymbol (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on ttf-opensymbol; however:
  Package ttf-opensymbol is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 2.2.0-1ubuntu5); however:

---

### Post by philinux on 2007-10-06
Solved it finally with 

touch  /usr/share/fonts/truetype/msttcorefonts
touch: setting times of `/usr/share/fonts/truetype/msttcorefonts': Permission denied
philcb@philcb-desktop:~$ sudo touch  /usr/share/fonts/truetype/msttcorefonts

Haven't got a clue what touch does - it says setting times :confused:

---

### Post by divali on 2007-10-06
Didn't help me. Heres my output:
after:

touch /usr/share/fonts/truetype/msttcorefonts
touch: setting times of `/usr/share/fonts/truetype/msttcorefonts': Permission denied
philcb@philcb-desktop:~$ sudo touch /usr/share/fonts/truetype/msttcorefonts

divali@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  fast-user-switch-applet gnome-backgrounds libwps-0.1-1 myspell-en-za
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openoffice.org-core
Recommended packages:
  nfs-common
The following NEW packages will be installed
  openoffice.org-core
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0B/35.5MB of archives.
After unpacking 101MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 130754 files and directories currently installed.)
Unpacking openoffice.org-core (from .../openoffice.org-core_2.2.0-1ubuntu5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_2.2.0-1ubuntu5_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_2.2.0-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
divali@ubuntu:~$

Any help anyone?

---

### Post by useResa on 2007-10-06
> **philinux said:**
> Haven't got a clue what touch does - it says setting times :confused:
From what I understand of [the description of touch]("http://linux.die.net/man/1/touch") modifies the time stamp of a file to the moment you "touch" it. Meaning that time and date of creation/modification are changed to the current time.
AFAIK if the time of creation/modification lies in the future (which can sometimes happen if you modify your local time) a file can not be accessed.

I mostly use touch to create a file that is not yet existing.
For example if you cd into your home directory and issue the command
```
touch touch_testfile.txt
```you will see that a file is created with the name touch_textfile.txt (provided it was non existent before giving the command ;)).

---

### Post by philinux on 2007-10-06
So those updates yesterday were timestamped wrongly?

Anyway I found the solution from a post back in april and theres a bug report for gutsy too.

---

### Post by divali on 2007-10-06
How did you solve the problem? Any help will be useful.

---

### Post by baja munda on 2007-10-06
Same here :

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  openoffice.org-style-default: Depends: openoffice.org-style-andromeda (= 2.2.0-1ubuntu5) but 2.2.0-1ubuntu4 is installed
E: Unmet dependencies. Try using -f.

---

### Post by philinux on 2007-10-06
[http://ubuntuforums.org/showpost.php?p=2401087&postcount=4](http://ubuntuforums.org/showpost.php?p=2401087&postcount=4)

You have to read it all it explains the procedure very well.

But your problem sounds different. I'd post a new thread with your particlular problem.

---

### Post by John Jason Jordan on 2007-10-10
I have what appears to be a related problem after the recent OOo updates. I had no problem installing the updates, but something has gone terribly wrong with Insert Special Character (from the menu and from the keyboard) in OOo. I use a lot of special characters and generally insert them in OOo Writer with Ctrl-Shift-u + hex code. This still works fine in all applications except OOo. In OOo it inserts the wrong character. For example, if I insert a u-umlaut (hex FC) it inserts the cedilla from the bottom of a c-cedilla. Here in Firefox (as in Abiword and Kword) it still inserts a ü. (See?) 

I have a paper due Thursday and I desperately need to fix this. I am guessing that it has something to do with the problems with ttf-opensymbol. I have completely uninstalled OOo and all of its parts and then reinstalled, to no avail. I tried a force version back to the ubuntu3 version, but that failed because evidently not all the components are still available.

I even tried to download and install the 2.3 version from OOo, but I'm on Feisty amd64 and all they have is an i386 deb. 

I've been struggling with this for three days and I'm out of time. Please someone HELP!

---

