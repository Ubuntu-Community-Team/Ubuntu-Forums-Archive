---
title: "very confused"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by nomb on 2006-08-11
Hello everyone, I've never used ubuntu before I've only used FC and suse but lately suse is becoming more and more buggy so I decided to give ubuntu a try.  I was very confused about sudo so for the time being I've made roots password.  I really want to get my wifi working so I'm trying to install ndiswrapper and aparently I don't have make.  so i did some research and I need to install qt3-dev-tools i think.  there are a lot of dependencies that I need is there a command that will install it for me.  please if someone would help me I would be very grateful.

thanks,

nomb

---

### Post by H.E. Pennypacker on 2006-08-11
Uhmm, I've never heard of something that installs any given dependencies without having a direction in mind.  You need to tell us exactly what you plan on doing, and we can possibly tell you what the dependencies are.  If you download a program, that program will most likely come with a list of its dependencies.

But really, I don't think there's some magic command that will install everything you need.  You may have to depend on Synaptic.  

See if there's a .DEB for ndiswrapper.  I don't think there is one.  Btw, doesn't Dapper come with ndiswrapper?  I believe it does.  I don't remember installing it.

---

### Post by nomb on 2006-08-11
when i do 

ndiswrapper 
and 
sudo ndiswrapper they both say command not found so I guess not

what I would like to do is be able to use the make command to compile and install software (like ndiswrapper)

---

### Post by dmizer on 2006-08-11
ndiswrapper is in the repositories.  are you sure your card is going to need the latest version of ndiswrapper?  if not, you can just find it in synaptic. 

if you're familiar with fc or rh, it might help to know that synaptic is debian's version of yum.

i've only ran into a few occasions where it was necessary to compile a program from source in ubuntu, and generally then you just follow the directions from the howto.  what card are you trying to get to work?

---

### Post by dmizer on 2006-08-11
> **nomb said:**
> when i do 

ndiswrapper 
and 
sudo ndiswrapper they both say command not found so I guess not

what I would like to do is be able to use the make command to compile and install software (like ndiswrapper)

if you are using the cli, you will have to use aptitude as follows:
```
sudo aptitude update&&sudo aptitude install ndiswrapper
```

---

### Post by nomb on 2006-08-11
broadcom 4311 on my dell

I used yast to install software automatically
however i did use yum a few times.  you said synaptic is like yum?
Do I have to run it from the terminal?

thanks sorry if i sound to noobish

---

### Post by user1397 on 2006-08-11
> **dmizer said:**
> if you are using the cli, you will have to use aptitude as follows:
```
sudo aptitude update&&sudo aptitude install ndiswrapper
```really?  i always thought it was ```
sudo aptitude update && sudo aptitude install ndiswrapper
```with those spaces infront of and behind the &&'s.  am i wrong or am i right?

---

### Post by nomb on 2006-08-11
this is what I got

```

nomb@nomb-laptop:~$ sudo aptitude update&&sudo aptitude install ndiswrapper
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Get:5 http://us.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Get:6 http://us.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Fetched 32B in 1s (24B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

```

is that cause I'm updating?

---

### Post by dmizer on 2006-08-11
> **erik1397 said:**
> really?  i always thought it was [snip] with those spaces infront of and behind the &&'s.  am i wrong or am i right?

no need for spaces.  try it yourself:
```
sudo aptitude update&&sudo aptitude upgrade
```

---

### Post by dmizer on 2006-08-11
> **nomb said:**
> this is what I got

```
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

is that cause I'm updating?

do you have synaptic open?  you can't use cli and synaptic at the same time because they lock eachother out.  if you want to use synaptic, just do a search for ndiswrapper.  if you want to use the cli, just close synaptic.  ie: one or the other but not both.

---

### Post by macca87 on 2006-08-11
Remember ubuntu is easy!... its so much easier than FC (not sure never used suse), anyways....

If you want to install make and gcc etc.. do
sudo apt-get install build-essential

Or use synaptic package manager to install build-essential.
Also that wrapper thing is on there too ive seen it. apt-get automatically handles dependancies.

---

### Post by dmizer on 2006-08-11
> **nomb said:**
> broadcom 4311 on my dell

I used yast to install software automatically
however i did use yum a few times.  you said synaptic is like yum?
Do I have to run it from the terminal?

thanks sorry if i sound to noobish

here's a good howto for getting your card installed: [http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+4311](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+4311)

from terminal to install software you can use:
sudo aptitude install programname
or
sudo apt-get install programname

you will see both in directions on this site.  the general concensus is that the prefered method is aptitude because it is more intelegent than apt-get.  i tend to agree after having used it for about a week now.

if you prefer a yast like gui interface, synaptic is in the system > administration menu.

all methods mentioned here are competent and fast.  i have not once run into a problem with them unless the repositories were down.

---

### Post by nomb on 2006-08-11
ok thanks a lot, i tried that guide and I couldn't get past 

 4B ) Extract your Cards firmware from the driver
Just to be safe we'l put the driver in the kernel folder too
Code:

sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-25-386 ~/Desktop/wl_apsta.o


I installed network manager but aparently it didn't get my driver installed
which is why i was gonna try ndiswrapper.  But I'd love not to have to use it if you have any ideas

thanks again your being a great help

nomb

---

### Post by dmizer on 2006-08-11
please post the output from cli of:
```
uname -r
```

---

### Post by nomb on 2006-08-11
im running kernel

2.6.15-23-386

(i know linux commands just not ubuntu :D )

---

### Post by dmizer on 2006-08-11
> **nomb said:**
> im running kernel

2.6.15-23-386

(i know linux commands just not ubuntu :D )

ok, you'll notice the command in the howto said thus:
```
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-25-386 ~/Desktop/wl_apsta.o
```
but your kernel is 2.6.15-23-386 so you'll have to modify this line to fit your kernel like so:
```
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-23-386 ~/Desktop/wl_apsta.o
```
a small change, but makes all the difference.

---

### Post by nomb on 2006-08-11
very true, i went ahead and did that but nothing happened... :confused:

---

### Post by dmizer on 2006-08-11
well, there are 11 pages of replies on that thread ... browse through there and see if you find your answer.  if not, post your problem there, and someone should pop in and tell you how to fix it.

unfortunately i really can't do too much else becaues i don't have your card, but i know you're at least on the right track now.  there's loads of helpful information in that thread.

---

### Post by nomb on 2006-08-11
ok thanks, got any experience installing ati drivers?

---

### Post by macca87 on 2006-08-11
I've been reading this thread and it seems alot of people like to do things the hard way.

On another note install ati drivers:
sudo apt-get install fglrx
will install the fglrx ati drivers for ubuntu.
You will need to enable the repository containing it, can't remmeber what it is, just google for ubuntu repositories and get multiverse,universe, and others u might need

---

### Post by nomb on 2006-08-11
I got this error:

nomb@nomb-laptop:~$ sudo apt-get install fglrx
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fglrx
nomb@nomb-laptop:~$

---

### Post by dmizer on 2006-08-11
you'll need to enable the multiverse/universe repositories.

check the wiki on how to do that here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by nomb on 2006-08-11
i have both multiverse and universe enabled but still no fgrlx
am i doing something else wrong?

---

### Post by dmizer on 2006-08-11
nope ... not doing anything wrong.  there is no such package.  but it gave me enough to do a decent search.  try this thread:
[http://www.ubuntuforums.org/showthread.php?t=143283&highlight=fgrlx](http://www.ubuntuforums.org/showthread.php?t=143283&highlight=fgrlx)

---

