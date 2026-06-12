---
title: "Automatix update issue."
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by crackling on 2006-12-10
I recently installed Automatix and I had a few issues during installation with the version being for Ubuntu 6.10 even though I was sure I downloaded 6.06 version. I got it to install eventually but now the update manager keeps prompting me to update to automatix 2 new version: 1.1-2.3-6.10edgy_i386. I'm running on 6.06 as mentioned before, so how do I get rid of this update. It prompts me to update everytime I boot up. I tried to uncheck it and close it but it still persists.

---

### Post by igknighted on 2006-12-10
Since there probably wont be any more choices added to the dapper version, I would remove the automatix repo from your sources.list file.  You already have the program, so you don't need the repo anymore.

---

### Post by crackling on 2006-12-10
I'm new to Linux so could you explain what a repo is and how to remove it? :D 
Thanks.

---

### Post by eriefisher on 2006-12-10
In a terminal type:

sudo gedit /etc/apt/sources.list

Find the line with automatix and place a # in front of it.

A repo is the place where the software is stored for you to download.

---

### Post by igknighted on 2006-12-10
Open a terminal window and copy/paste the following into there and type enter:
```
gksudo gedit /etc/apt/sources.list
```
Then a box will pop up asking for your admin password - it is the same as your normal password.  Then a text editor will open.  Paste its contents here and I'll tell you what lines you need to delete.

---

### Post by crackling on 2006-12-10
From gksudo gedit /etc/apt/sources.list:
```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://www.getautomatix.com/apt edgy main
deb http://www.getautomatix.com/apt dapper main
deb http://www.getautomatix.com/apt dapper main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper multiverse
#AUTOMATIX REPOS END

```

---

### Post by igknighted on 2006-12-10
Ok, put a # sign a the beginning of three lines that say [www.getautomatix.com](www.getautomatix.com).  This will tell Ubuntu not to check those servers for updates.  If you want, you could leave one of the dapper ones un-commented (thats the programming term for the # sign in front of the line), and you shouldn't have the update problem.  It's the edgy line that is the problem.  This way, if they do update the dapper version you would get that update.  Finally, after you save and close the file, type 'sudo aptitude update' in the terminal so it can update the list of packages available.  You shouldn't have this issue any more.

---

### Post by ciscosurfer on 2006-12-10
> **igknighted said:**
> Since there probably wont be any more choices added to the dapper version, I would remove the automatix repo from your sources.list file.  You already have the program, so you don't need the repo anymore.This isn't necessarily true.  They may not add any new apps (even this is debatable), but they certainly update the versions of apps to later versions from time to time.  That being said, if you don't want Apt to check for newer versions each time you run an update, you can definitely comment out the line for the time being and uncomment it from time to time when you want to check for newer versions.

---

### Post by arnieboy on 2006-12-10
Delete the following lines from sources.list:
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
and make sure u have only one copy of the automatix dapper repo added.
now do:
```
sudo apt-get remove automatix2
sudo apt-get clean
sudo apt-get update
sudo apt-get install automatix2
```

---

### Post by igknighted on 2006-12-10
^^^Listen to him, he wrote automatix... he knows what you need^^^

---

### Post by crackling on 2006-12-10
> **arnieboy said:**
> Delete the following lines from sources.list:

and make sure u have only one copy of the automatix dapper repo added.
now do:
```
sudo apt-get remove automatix2
sudo apt-get clean
sudo apt-get update
sudo apt-get install automatix2
```

Just to make sure, is this what I should do?
```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://www.getautomatix.com/apt dapper main

```
deleted deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deleted deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main


Leave the following alone?
```

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper multiverse
#AUTOMATIX REPOS END
```

---

### Post by arnieboy on 2006-12-10
yes you are doing it right.

---

### Post by crackling on 2006-12-10
Okay, thanks everyone!:KS

---

