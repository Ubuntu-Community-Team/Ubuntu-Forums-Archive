---
title: "I think I broke it..."
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by destromofia on 2006-09-13
so I was reading up on maybe getting a firewall installed, I went to a sight that gave an apt-get line for installing said firewall.

Instead of typing this line in the terminal, I stuidly added to to the apt line in synaptic, but since it isn't a reposotory, I now get this error when I just start up synaptic:

E: Type 'apt-get' is not known on line 37 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I went to the source list to try and delete the lines that are wrong, but it is write protected. 

Any help please?

---

### Post by jordanmthomas on 2006-09-13
```
gksudo /etc/apt/sources.list
```
This will allow you to edit the file.

If you want, you can post the results of
```
cat /etc/apt/sources.list
```
and we can help you in case you get stuck fixing your sources.list

---

### Post by destromofia on 2006-09-13
## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

# deb [http://apt.filefind.net/](http://apt.filefind.net/) breezy main contrib non-free
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

apt-get install gnome-lokkit
apt-get install gnome-lokkit

I know..or at least am pretty sure, that its that apt-get install gnome-lokkit thing, because that where I screwed up. 

even after using your first command though, I still cant delete that out of the file, what do I need to do?

---

### Post by jordanmthomas on 2006-09-13
Indeed it is messed up.
I forgot (yet again) to put part of the command
```
gksu [COLOR="Red"]gedit[/COLOR] /etc/apt/sources.list
```

Delete those apt-get lines, save, and type this on the command line
```
sudo apt-get update
sudo apt-get install gnome-lokkit
```

---

### Post by jcrnan on 2006-09-13
try:

sudo gedit /etc/apt/sources.list

edit: beaten to it :)

---

### Post by Linux Lover on 2006-09-13
If you really have broken your repository, then you may do the following.
This is a complete repository list for apt-get in ubuntu 6.06 (Dapper Drake).

1. First take a back up copy of your existing sources.list file,
**$ mv /etc/apt/sources.list /etc/apt/sources.list.old**

2. Now create the new file
**$ gksudo gedit /etc/apt/sources.list**

3. Copy-paste the following in the file and save it. [COLOR="Red"]Make sure to hit a return at the last line for an extra blank line.[/COLOR]
---> Copy the following portion up to the end and paste it in /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

## Bleeding edge wine repository for Dapper
## only uncomment it if you need it
## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## skype
## only uncomment it if you need it
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

---

### Post by destromofia on 2006-09-13
Thank you so much, I would be lost without the help I get in these forums.

---

### Post by jordanmthomas on 2006-09-13
Me too.

---

### Post by nalmeth on 2006-09-13
sudo gedit /etc/apt/sources.list

you should typically backup this file before you edit it, in case you can't recall what changes were made

EDIT: nevermind :)

---

