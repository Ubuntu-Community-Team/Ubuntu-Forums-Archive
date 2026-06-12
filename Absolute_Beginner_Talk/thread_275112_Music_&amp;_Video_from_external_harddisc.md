---
title: "Music &amp; Video from external harddisc"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2006-10-10
uh oh... what did i get myself into... i have no idea what I'm doing.  I'm trying to figure out how to play music and movies I have on my external hard drive, but I don't know the first thing about ubuntu... please help!! lol

---

### Post by divague on 2006-10-10
This guide will help you

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

---

### Post by 3rdalbum on 2006-10-10
[http://www.getautomatix.com](http://www.getautomatix.com).

Install Automatix, run it, and it will install the restricted codecs.

---

### Post by familyjules74123 on 2006-10-10
ok so im trying it... but it says that it couldn't find the package

---

### Post by JayTee on 2006-10-10
you most likely don't have the repository for Automatix in your sources list.
Open a terminal and type the following:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo gedit /etc/apt/sources.list
Copy and paste the following line at the end of the file 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
then close the editor and go back to the terminal and type the following lines.
sudo apt-get update
sudo apt-get install automatix

and that should get the package and install it.
Then click on the Applications menu and go to System Tools and click on Automatix to run it. It will give you a list of a lot of things to install and one of them will be the w32codecs.
Good luck!

---

### Post by familyjules74123 on 2006-10-10
ok i did that... and on the second to last command it says its connecting to package and it just stays at 99%


edit -  well spoke too soon... it finally did something... that was fail to connect

---

### Post by Hmarroqu on 2006-10-10
I used easy ubuntu

[http://ubuntuguide.org/wiki/Dapper#How_to_use_Easy_Ubuntu](http://ubuntuguide.org/wiki/Dapper#How_to_use_Easy_Ubuntu)

and go to Applications- add/remove and find "Kaffeine" its great for everything.


[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) is a great site for learning how to do many many things. and it has all the stuff u have to type in the commands!

i lub it:-D

---

### Post by familyjules74123 on 2006-10-11
> mike@mike-laptop:~$ sudo gedit /etc/apt/sources.list
mike@mike-laptop:~$ wget [http://easyubuntu.cafuego.net/969F3F57.gpg](http://easyubuntu.cafuego.net/969F3F57.gpg) -O - | sudo apt-key add -
--00:16:25--  [http://easyubuntu.cafuego.net/969F3F57.gpg](http://easyubuntu.cafuego.net/969F3F57.gpg)
           => `-'
Resolving easyubuntu.cafuego.net... 209.59.209.80
Connecting to easyubuntu.cafuego.net|209.59.209.80|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,415 (2.4K) [text/plain]

100%[====================================>] 2,415         --.--K/s

00:16:46 (32.57 KB/s) - `-' saved [2415/2415]

gpg: no ultimately trusted keys found
OK
mike@mike-laptop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:3 [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Get:5 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg [189B]
Get:6 [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release [5753B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Get:7 [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release [9452B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Fetched 15.6kB in 0s (17.2kB/s)
Failed to fetch [http://easyubuntu.cafuego.net/dists/main/Release](http://easyubuntu.cafuego.net/dists/main/Release)  Unable to find  expected entry  easyunbuntu/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following sign atures couldn't be verified because the public key is not available: NO_PUBKEY F 120156012B83718
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.
mike@mike-laptop:~$ sudo apt-get install easyubuntu
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package easyubuntu


thats what it says in terminal when i try to install easyunbuntu

---

### Post by nalmeth on 2006-10-11
Is your external HD picked up and mounted fine? Can you browse thru it?

[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) 
Explains why restricted formats aren't setup out-of-the-box, and provides instructions for manually installing those codecs.

Automatix and EasyUbuntu have been recommended, they are simply scripts made to automate the installation of these codecs, BUMPS is another one.

Basically, either follow the instructions on the wiki page, or follow the instructions for the scripts.

---

### Post by familyjules74123 on 2006-10-11
i think it is mounter fine... i can browse through it... and msuic even gets selected from it in media programs... it just doesnt play it.

I got that error on both easyubuntu and automatix

---

### Post by Perfect Storm on 2006-10-11
Title of the thread changed to something better.

---

