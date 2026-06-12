---
title: "apt get broken - still point to E drive"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by nickburns on 2007-07-21
I have a fresh install of ubuntu on a server.  I have removed the first two lines of 

/etc/apt/souces.list

that point to the cd drive.  I have also uncommented out all the repos in the file, and sudo apt-get updated several times.

The problem is that if I try to sudo apt-get install phpmyadmin it returns:

E: Couldn't find package phpmyadmin


It is like it still is pointing to the E drive, any help...?

---

### Post by nickburns on 2007-07-21
Here is my sources.list file:



deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by Nythain on 2007-07-21
that doesnt mean its pointing to the e drive, that means Error :) basically its not finding the package you are trying to install... make sure you have all of the repo's in your sources.list enabled (uncomment by removing the #) then type sudo update and try to install again... if it still cant find the package, it might not be in any of the official repo's, though im sure it is

---

### Post by endersshadow on 2007-07-21
E stands for error

Have you enabled Universe in your sources.list file?

P.S.-You can search for a package using this command:

```
apt-cache search php admin
```

php and admin are treated here as keywords.

---

### Post by endersshadow on 2007-07-21
Edit: Inaccurate info...my fault.

---

### Post by Nythain on 2007-07-21
according to [http://packages.ubuntu.com](http://packages.ubuntu.com) it lies in the universe repo wich you have enabled... did you forget to sudo apt-get update after removing the cdrom entries in your sources.list???

---

### Post by nickburns on 2007-07-21
I have updated, upgraded 20 times.

I even copied the file out of the folder, updated, upgrated and moved the file back.  It will go through and update with no problems but no phpmyadmin.

Even if I type sudo apt-get install phpm and hit tab it does not show any options.

Very strange...

---

### Post by nichipet on 2007-07-21
For what it's worth, is apt-get having trouble with other packages? Can the problem be isolated to phpmyadmin or is apt-get completely broken?

---

### Post by nickburns on 2007-07-21
Here is the tail of the update:

....
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources


So it is update-ing, is there a way to clean the apt-get update files???

---

### Post by nickburns on 2007-07-21
I can see other packages in the universe like libphp-adodb that I think live the universe.

---

### Post by nickburns on 2007-07-21
If I try to install anything in universe it says:


aaron@phpserver:/etc/apt$ sudo apt-get install libphp-adodb
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libphp-adodb is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libphp-adodb has no installation candidate

---

### Post by nickburns on 2007-07-21
I finally got it....

I had to comment out all repositories, then bring them in two at a time, updating each time.

Thanks for the help.

---

