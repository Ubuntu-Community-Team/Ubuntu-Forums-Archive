---
title: "Gaaahh! I can't install programs"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by CAX on 2006-06-22
I have just installed Kubuntu 6.06 and that went really smooth. However since then I tried (for days) to install programs. To update the list in the Konsole went ok but the it can never find the packages which is irritating but ok so I tried the graphical way with Adept installer and searched for eg. firefox that I wanted to install but then I cannot mark the box next to firefox once it has found it as it is grey and not active. SO in desperation I downloaded Opera since it is available as a hmm is it deb-file or something which I downloaded and actually manage to install (well it asked if I wanted to install the package when I clicked on it) but now I cannot find it anywhere.  I have read a lot of guides and so far nothing has worked. I mean to just retype comands is pretty easy and I actually managed to update the list or something of available programs or something but that's about it. I think it should be something that I haven't thought about that will solve all problems just that I cannot find out what on my own. All help greatly appreciated!

Cheers,

CAX:confused:

---

### Post by aysiu on 2006-06-22
Instead of describing the errors, can you post back actual output from the terminal? Please copy and paste the output of these commands: ```
cat /etc/apt/sources.list
sudo aptitude update
sudo aptitude install firefox
```

---

### Post by CAX on 2006-06-22
cat /etc/apt/sources.list gave following:

## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
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

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

the update command gave:

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Reading package lists... Done

install command gave 

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
No candidate version found for firefox
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


One difference though as I have been writing sudo apt-get install firefox .

Really appreciate the help. Thanks!

EDIT: looks like all my sources has been edited out no?

---

### Post by nalmeth on 2006-06-22
sudo nano /etc/apt/sources.list
Remove the # from the start of all the repositories
sudo aptitude update
sudo aptitude install firefox

---

### Post by CAX on 2006-06-22
hmm when I type sudo nano /etc/apt/sources.list I just get a blank page. Does that mean that my source list is empty? If I would past in the correct one how do I save it then? under settings -> save as defaults of settings->save session profile ?

Honestly I am soo lost that I really feel like an idiot (especially since I once waaay back studied AI and programming).

Thanks for the help.

---

### Post by aysiu on 2006-06-22
It shouldn't be blank unless you're typing the name wrong. Copy and paste this command just to be sure: ```
sudo nano /etc/apt/sources.list
``` If it blank, so be it--let's populate it.

---

### Post by CAX on 2006-06-22
hmm not sure how I manage to type the wrong command twice but somehow I did. When I copied the command it worked. But how do I save it now after changing?

---

### Post by nalmeth on 2006-06-22
Cntl-x
y
Enter

---

### Post by CAX on 2006-06-22
Thanks a lot! Everything is working now but I guess I'll run into other problems later on so I'll be back :P

Cheers,

CAX

---

