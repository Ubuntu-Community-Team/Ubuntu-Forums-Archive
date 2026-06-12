---
title: "Automatix cant find package"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-09-19
I get through the key import part fine but when I do the upgrade it says it cant find the packages.

---

### Post by croak77 on 2006-09-20
What are you installing? Is that the full message?

---

### Post by voodoonirvana on 2006-09-20
Ok, so im using this:

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_Ubuntu_5.10_Breezy_Badger](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_Ubuntu_5.10_Breezy_Badger)

And when I type in "sudo apt-get install automatix" it tells me that it couldn't find the package. Oh and Im on Breezy.

---

### Post by Metacarpal on 2006-09-20
Since Automatix opted to move its support forum off of the Ubuntu boards (they're multi-platform now), you might have an easier time finding an exact solution to your Automatix problem [there]("http://www.getautomatix.com/forum/").

That being said, we can probably help you anyway. :D

Did you edit your sources.list file as shown on that page?

Alternately, since all Automatix does is install things for you that can be done for yourself, if you tell us what you'd like installed, we can give you instructions to do it without installing Automatix.

---

### Post by voodoonirvana on 2006-09-20
> **Metacarpal said:**
> Since Automatix opted to move its support forum off of the Ubuntu boards (they're multi-platform now), you might have an easier time finding an exact solution to your Automatix problem [there]("http://www.getautomatix.com/forum/").

That being said, we can probably help you anyway. :D

Did you edit your sources.list file as shown on that page?

Alternately, since all Automatix does is install things for you that can be done for yourself, if you tell us what you'd like installed, we can give you instructions to do it without installing Automatix.

Well I cant watch anything that needs quicktime or anything that is .mov, can you help me with that? I think I need the windows media codecs, either that or the encoders...something like that.

---

### Post by voodoonirvana on 2006-09-20
Some help please?

---

### Post by Metacarpal on 2006-09-21
Sorry for the delayed response.  Here's what to do to get the various extra codecs installed:

Open a Terminal (Applications menu > accessories > terminal) and type:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
It'll ask you for a password. Enter your regular login password.  Then,
```
gksudo gedit /etc/apt/sources.list
```
This will open a text editor file.  Replace the entire contents of that file with the following:
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free 
```

Then Save and Close that file.  Back in terminal, enter the following:
```
sudo aptitude update
```
then
```
sudo aptitude install totem-xine gxine libxine-main1 libxine-extracodecs w32codecs
```
and that ought to fix you up!  :)

---

