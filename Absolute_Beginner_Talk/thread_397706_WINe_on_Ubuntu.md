---
title: "WINe on Ubuntu?"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-03-31
I can't find WINe in the pkg installer, am I missing it or is it gone?

---

### Post by InuyashaDuelist on 2007-03-31
Just open up a console window and type in

```
sudo apt-get install wine
```

---

### Post by david_kt on 2007-03-31
> **InuyashaDuelist said:**
> Just open up a console window and type in

```
sudo apt-get install wine
```

It will not work I guess. First of all, you need to enable additional repository i.e. "universe" repository. After that you must reload, and then you can fine wine, either from synaptic or using above code.

DK

---

### Post by Maestro23 on 2007-03-31
As David_kt stated, wine is in the repositories.  You must enable some extras on your system.

Enabling Repositories: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by kc5hwb on 2007-03-31
Whats the command to enabled the Universe Repository?

---

### Post by Maestro23 on 2007-03-31
> **kc5hwb said:**
> Whats the command to enabled the Universe Repository?

Use the link above for GUI or use Command Line:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by InuyashaDuelist on 2007-03-31
Open up Synaptic and go to Settings/Repositories. Check the box next to the Universe repository to enable it. Then press OK, reload, and install Wine using the command I provided above.

I had assumed you had already enabled the universe repository, I apologize for confusing you.

---

### Post by kc5hwb on 2007-03-31
No apology necessary, you have been quite helpful.  Thanks for your replies.

---

### Post by splendid on 2007-04-11
Trying to load wine and get following message:

ob@basement:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://repos.knio.it](http://repos.knio.it) breezy/main Packages (/var/lib/apt/lists/repos.knio.it_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://repos.knio.it](http://repos.knio.it) breezy/contrib Packages (/var/lib/apt/lists/repos.knio.it_dists_breezy_contrib_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://repos.knio.it](http://repos.knio.it) breezy/non-free Packages (/var/lib/apt/lists/repos.knio.it_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package wine has no installation candidate


Any ideas?

---

### Post by splendid on 2007-04-14
Now I am receiving the following message after I enter the sudo apt-get install wine command:

rob@basement:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

Any ideas???

---

### Post by Patrick K on 2007-04-14
Wine is updated on an almost daily basis. It could be the server is down or they are updating when you tried. Wait a while then try again.

---

### Post by splendid on 2007-04-14
Tried again.  Several times.  Still get same message.

---

### Post by Maestro23 on 2007-04-14
> **splendid said:**
> Tried again.  Several times.  Still get same message.

Can you post your /etc/apt/sources.list ?

> cat /etc/apt/sources.list

---

### Post by splendid on 2007-04-14
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe

---

### Post by david_kt on 2007-04-15
> **splendid said:**
> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe

gksudo gedit /etc/apt/sources.list

and then remove # from

```
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
```

and add this lin as well:
```
deb http://us.archive.ubuntu.com/ubuntu[/url] breezy universe
```

After that:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine
```

one at a time.

DK
DK

---

### Post by splendid on 2007-04-15
David,

Thanks for your help.  I followed your instructions, and now am receiving the following message:

rob@basement:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu%5b_url%5d_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package wine has no installation candidate

---

### Post by david_kt on 2007-04-15
May you should try another source,  add below repository in your sources.list:

```
deb http://wine.budgetdedicated.com/apt breezy main
deb-src http://wine.budgetdedicated.com/apt breezy main
```

and then open terminal and run below command:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

and after that

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine
```

DK

---

### Post by YokoZar on 2007-04-15
1) Breezy is really old and you need to upgrade soon.  You also won't be able to get current Wine packages with it.
2) You need to be using the 32-bit version.  Looks like you're either running 64-bit or ppc.

---

### Post by splendid on 2007-04-15
Yes, I have an AMD 64 bit processor and am using the 64 bit version of Breezy.  What is the safest way to upgrade?  I have ssh, apache, and ftp server all up and functional.  Want to make sure I don't break something in the process.

Thanks to everyone for all the help!!!!

---

