---
title: "Package Manager Error, Reinstall?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by dacookiemonn on 2007-06-02
man, its just one thing after another and im gonna get upset if I have to reinstall this thing again.  I followed some directions to get automatix2 and everthing seemed to go good.  Nothing worked, and now I got this error icon at top.  I can not access the package manager now.
___________________________-
[COLOR="Blue"]
When I left click on the icon at top I get this:[/COLOR]

[COLOR="Red"]A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 46 in source list /etc/apt/sources.list, E:The list of sources could not be read.'[/COLOR]
________________________--
[COLOR="Blue"]When I right click and select start package manager I get this:[/COLOR]

[COLOR="Red"]E: Type '“deb' is not known on line 46 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/COLOR]

---

### Post by dacookiemonn on 2007-06-02
i also did apt-get check and get this:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Any solutions

I also now think my sources.list file is missing, when i apty-get update it says it cant read it, so I go there and sure enough, its gone.
I cant believe installing a simple piece of software would allow for the file to be deleted

---

### Post by Nythain on 2007-06-02
gotta love that automatix... so whats your /etc/apt/sources.list file look like???
sounds like there's a typo somewhere (well line 46 to be precise).

as for the other problem, maybe it will go away after we fix the first problem, maybe not, we'll get to that when we figure out whats up with line 46

---

### Post by Nythain on 2007-06-02
ok, so just re-read that, second problem probably lies in the fact that you need to throw a sudo in front of apt-get

---

### Post by dacookiemonn on 2007-06-02
file is there i was looking in wrong place.  I added sudo in front of apt-get update and sill got the line 46 error.

sources.list look like this:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”

---

### Post by dacookiemonn on 2007-06-02
i also did this, cuase i seen it somewhere in regard to the second error i got.

sudo chmod 644 /etc/apt/sources.list

do i need a different value?

---

### Post by Nythain on 2007-06-02
ok, first off... the " on the last line are your major problem, delete those... dont think you really should have chmod'd the file, but i dont think it will hurt anything, hopefully

like i said the second problem was caused because you didnt run with sudo... apt-get, aptitude, and dpkg all need sudo

---

### Post by forestpixie on 2007-06-02
I think the " in front of 

&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main&#8221;

should be a # to comment it out - or nothing to get the repo
like 

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

or

#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

I'm sure someone will say if I'm wrong

---

### Post by forestpixie on 2007-06-02
Looks like I'm learning! Just trying to be helpful - but not quick enough.

---

### Post by dacookiemonn on 2007-06-02
ok i did that but can not save it.  read only.  Im looking into, hopwfully i can just chmod it higher or something
________
OK i ran gksudo gedit /etc/apt/sources.list and was able to save it and now all works good, thanks for the help

---

### Post by forestpixie on 2007-06-02
you need to edit file as sudo then you'll be able to save it

---

### Post by Nythain on 2007-06-02
stop chmod'n the file... in terminal just type gksudo gedit /etc/apt/sources.list and make the changes

---

### Post by dacookiemonn on 2007-06-02
I think im getting the hang of this.  I have absolutely 0 Linux experience.  Just live knoppix 2 years ago for about 1 hour.  I thought whoaaaa WTF.  But ya its looking good.

---

### Post by Nythain on 2007-06-02
groovy... glad to hear you are diggin it... just remember, sudo and gksudo are your friends... so did you finally get those two quotes removed????

---

