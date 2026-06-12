---
title: "repositories!!!! trouble"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Siddy on 2006-12-18
well everytime i try to add something to the repositories it always comes up with an error saying: 

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

i have tryed to install wine and java but no matter what it keeps saying that. i have ubuntu 6.06 and a wireless internet connection.

Whats the problem???
and one more thing, can wine run all programs that are made for windows???

---

### Post by Voxxi on 2006-12-18
Post your /etc/apt/sources.list:

Open up a terminal and paste in:
```
cat /etc/apt/sources.list
```

Post the result of that command.

---

### Post by Siddy on 2006-12-18
> **Voxxi said:**
> Post your /etc/apt/sources.list:

Open up a terminal and paste in:
```
cat /etc/apt/sources.list
```

Post the result of that command.

sorry man im new to ubuntu...
whats a terminal and how do i get to it?

---

### Post by stupidkid on 2006-12-18
Applicatons -> Accessories -> Terminal

---

### Post by mid_night gypsy on 2006-12-18
Howdy Siddy,
  A terminal is a window box looking program,In time you will in up loving this program,it is where you can type commands.Such as "cat /etc/apt/sources.list". Which is the command to show you that file. So to answer your question where is the terminal ," go to Applications = Accessories = Terminal ( a TV looking icon).
                                                                                                          Much Luck, Gypsy[LEFT][/LEFT]

---

### Post by Siddy on 2006-12-18
thanks guys here it is,

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by Sef on 2006-12-18
> and one more thing, can wine run all programs that are made for windows???

No.  It can run many of them to varying degrees, but not all of them.   Read about [WINE]("http://winehq.com").

---

### Post by mid_night gypsy on 2006-12-18
Siddy 
 I just read your first post 'bout wine and java.It might be easier using a program call Automatix (yes with an X).
It's another installing program. [http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38) 
                                                                                                                                         gypsy

---

### Post by d3v1ant_0n3 on 2006-12-18
>  ```
apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts
```

Remove that line from your sources list.

Here's how:

Open the terminal again (Applications>Accessories>Terminal), and copy/paste this command into it:

```
sudo gedit /etc/apt/sources.list
```

This will open up gEdit text editor with your sources.list file, which contains a list of all your software sources.

Scroll down til you see the line I highlighted, and remove it.

Then click the 'save' button, and close out gEdit.

The line you removed is actually a terminal command to install java.

---

### Post by Sef on 2006-12-18
Delete this line: apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts

Apt-get is to be used in the terminal to install or remove software.

Uncomment (remove the #) before the following lines:

# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


To install java, read [Adding Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu").  Java is currently in multiverse.

---

### Post by pormogo on 2006-12-18
[i][http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main


[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main[/i]

make sure you have [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main prefixed by apt and listed only once in sources.list, it should look like

*deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main*

---

### Post by Siddy on 2006-12-18
lol whats the problem? i typed in sudo gedit /etc/apt/sources.list
and then it asked for my password and i typed it in but it wouldnt type? then i pressed enter and it said sorry try again!
i was typing the same password as when i turn the computer on!

---

### Post by Siddy on 2006-12-18
thanks again guys!!
now should everthing be ok

---

### Post by d3v1ant_0n3 on 2006-12-18
> **Siddy said:**
> lol whats the problem? i typed in sudo gedit /etc/apt/sources.list
and then it asked for my password and i typed it in but it wouldnt type? then i pressed enter and it said sorry try again!
i was typing the same password as when i turn the computer on!

When you type in your password in terminal, it's invisible- an added precaution (I presume) to stop people looking over your shoulder and seeing how many characters are in your password.

---

### Post by ciscosurfer on 2006-12-18
Once you have your Universe (for Wine from the Universe repo...if you'd like to use a different repository, see below) and your Multiverse (for Java) repositories enabled ([see here to enable them]("http://psychocats.net/ubuntu/sources")), go to a Terminal and enter in the following (copy and paste is the easiest)```
sudo aptitude update
sudo aptitude install sun-java5-jre sun-java5-bin sun-java5-plugin
```Follow the prompts, accept the licence, and choose yes to install (you can move around using the Tab button).  Once Java has been installed, enter the following in a Terminal to link up Java to use the version you just downloaded```
sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
```For Wine, you can enable the Universe repo or set a new repo to the following```
sudo gedit /etc/apt/sources.list

AND THEN ADD THE FOLLOWING LINE TO THE LIST:

deb http://wine.lowvoice.nl/apt dapper main

SAVE AND EXIT THE FILE
```Now, from a Terminal, issue```
sudo aptitude update
sudo aptitude install wine
```After Wine has been installed, type into a Terminal **winecfg** to configure Wine for usage.  You can learn more about Wine at the main Wine web site: [http://www.winehq.com/](http://www.winehq.com/)

---

### Post by Siddy on 2006-12-18
> **ciscosurfer said:**
> Once you have your Universe (for Wine from the Universe repo...if you'd like to use a different repository, see below) and your Multiverse (for Java) repositories enabled ([see here to enable them]("http://psychocats.net/ubuntu/sources")), go to a Terminal and enter in the following (copy and paste is the easiest)```
sudo aptitude update
sudo aptitude install sun-java5-jre sun-java5-bin sun-java5-plugin
```Follow the prompts, accept the licence, and choose yes to install (you can move around using the Tab button).  Once Java has been installed, enter the following in a Terminal to link up Java to use the version you just downloaded```
sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
```For Wine, you can enable the Universe repo or set a new repo to the following```
sudo gedit /etc/apt/sources.list

AND THEN ADD THE FOLLOWING LINE TO THE LIST:

deb http://wine.lowvoice.nl/apt dapper main

SAVE AND EXIT THE FILE
```Now, from a Terminal, issue```
sudo aptitude update
sudo aptitude install wine
```After Wine has been installed, type into a Terminal **winecfg** to configure Wine for usage.  You can learn more about Wine at the main Wine web site: [http://www.winehq.com/](http://www.winehq.com/)


with the java thing i typed in: sudo aptitude update
sudo aptitude install sun-java5-jre sun-java5-bin sun-java5-plugin
it said nothing about intalling, a license...


this is what it said: sid@sid-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release [34.8kB]
Get:7 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release [4886B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:8 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages [1889B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [43.7kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  404 Not Found
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [23.3kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [5419B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages [619kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages [4571B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources [255kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages [2458kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources [975kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [129kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [47.9kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [13.0kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [41.8kB]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [2508B]
Fetched 4835kB in 1m48s (44.5kB/s)
Reading package lists... Done



then i typed in: 


sid@sid-desktop:~$ sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-s un/jre/bin/java
update-alternatives: Cannot find alternative `/usr/lib/jvm/java-1.5.0-sun/jre/bi n/java'.


update-alternatives: Cannot find alternative `/usr/lib/jvm/java-1.5.0-sun/jre/bi n/java'.




SO yeah...its a bit weird

---

### Post by Siddy on 2006-12-18
just then i was trying to download wine from: 
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

it came up with this error:

[http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/source/Sources.gz:) 404 Not Found
[http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/source/Sources.gz:) 404 Not Found

---

### Post by Siddy on 2006-12-18
and when i tryed to do it your way ciscosurfer this is what it said:
plz plz help...


sid@sid-desktop:~$ sudo aptitude update
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release.gpg
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  404 Not Found
Fetched 5B in 7s (1B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache
sid@sid-desktop:~$ sudo aptitude install wine
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
sid@sid-desktop:~$ winecfg
bash: winecfg: command not found
sid@sid-desktop:~$

---

### Post by ciscosurfer on 2006-12-18
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?This means you have package manager open.

Try to run through the steps I provided again.

*After you get Java installed*, and after you enter in```
sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
```you will get the following line in your terminal saying:```
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
```And the freeconrib link apparently is down at the moment.

Please post back and someone should be able to assist you if I can't.

Good luck!

---

### Post by Siddy on 2006-12-19
sorry but instead of saying:
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.

it says: sid@sid-desktop:~$ sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
update-alternatives: Cannot find alternative `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java'.

---

### Post by Siddy on 2006-12-19
hey ciscosurfer thanks alot man i figured it out, the java thing is installing! thanks soooo much.:D :D

---

### Post by ciscosurfer on 2006-12-19
> **Siddy said:**
> hey ciscosurfer thanks alot man i figured it out, the java thing is installing! thanks soooo much.:D :DThat's great!  Glad you got it all worked out!

---

