---
title: "Help!"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by psyb0rg on 2006-11-25
I was just trying to use the Synaptic Package Manager to install a DVD codec.
I played around a little, added the repository, but when I click RELOAD, it tells me the following errors were found on your computer:
E: Type 'sudo' is not known on line 33 in source list /etc/apt/sources.list
E: Unable to lock the list directory
Go to the repository dialogue to correct the problem.

Now where is this repository dialogue? What do I do there?

Another issue that seems related is when I click on Applications> Add/Remove it gives the following error:

**Failed to check for installed and available applications**

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

HELP!:-|

---

### Post by xyz on 2006-11-25
Copy/Paste this in a terminal and post the output please:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by DougieFresh4U on 2006-11-25
gksudo gedit /etc/apt/sources.list from terminal,and copy & paste and  post it for us

---

### Post by psyb0rg on 2006-11-25
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

---

### Post by CaveRat on 2006-11-25
You might want to check out this link: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by taurus on 2006-11-25
> **psyb0rg said:**
> deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted
# deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine
Remove the last three lines in your /etc/apt/sources.list because they are all wrong.  If you want to install codecs and what not, yse Automatix2...

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by Tomosaur on 2006-11-25
The last 3 lines in your sources.list file are not 'wrong', they are just out of context completely. Those 3 lines are commands, and not repository listings. If you used those commands in the terminal, then they would work. You need to remove them from the sources.list file, and then use them in the terminal as you would any other command. The sources.list file is a listing of repositories.

---

### Post by psyb0rg on 2006-11-25
I tried removing the lines but got this error :s  :

"You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again."

PS.The left panel list in Synaptic is also empty now...

---

### Post by taurus on 2006-11-25
Applications -> Acceesories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

