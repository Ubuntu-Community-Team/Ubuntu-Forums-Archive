---
title: "Want to go from Breezy to Dapper"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by DCJoeDog on 2006-03-21
OK, the XGL and such have got me salivating, should I just go and do a 

#sudo apt-get dist-upgrade

or should I wait, also will I have to reinstall all my apps if I upgrade?

---

### Post by AndrewCaul on 2006-03-21
If you're uncertain, it's probably better to wait.

---

### Post by DCJoeDog on 2006-03-21
I'm no stranger to alpha/beta builds of OS's
xp/vista beta tester here, are there any steps I shouls know in upgrading?
also, will this reformat my CURRENT installation of Ubuntu or just upgrade it?
will there be things that just need changing afterwords like Repositories list and such, or will the new build have it's own list in place to take over?

---

### Post by Brunellus on 2006-03-21
I'd wait.  the dist-upgrade process is not terribly smooth (or wasn't last week, when I made the switch).  If you're posting here in the newbie forum, you probably shouldn't be using dapper until June.  

HOWEVER

if you are ready to deal with possible dist-upgrade issues (not so many nasty crashes once you're through, incidentally--but the dist-upgrade can be hairy) then:

edit /etc/apt/sources.list

comment out the backports and any other 'extra' repositories.  you should be left with just the regular ubuntu ones:  main, universe, multiverse.

Now change all references to "breezy" to read "dapper"

save.  

sudo apt-get update

sudop apt-get dist-upgrade

and leap down the rabbit-hole.

it won't reformat anything, but it won't hurt to back up data that you can't live without.

---

### Post by dermotti on 2006-03-21
My dist-upgrade went flawless.....

---

### Post by az on 2006-03-21
[QUOTE=DCJoeDog]I'm no stranger to alpha/beta builds of OS's
xp/vista beta tester here, are there any steps I shouls know in upgrading?
also, will this reformat my CURRENT installation of Ubuntu or just upgrade it?
will there be things that just need changing afterwords like Repositories list and such, or will the new build have it's own list in place to take over?[/QUOTE]

If you pop in the cd and boot it, it will offer you the choice of installing next to your current install (if there is sufficient disk space) or wiping the drive and starting from there.

If you boot your ubuntu installaltion and insert the cd, it will ask you if you want to install the packages from that cd (upgradeing your system).  If you have a lof of stuff from universe, which is not on the cd, you upgrade will be incomplete and may not work.  You really need to change you repositories.  Just rename the "breezy" to "dapper" in all of your current repositories (you can use synaptic for that) and refresh you packages and dist-upgrade (smart upgrade)

So, to answer your question, you have a choice.

Please report bugs that you find that have not already been reported.
[https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by DCJoeDog on 2006-03-21
well the worst thing that can happen is I have to install Ubuntu again, that doesn't scare me, I reinstalled windows at a regular basis just to keep things tidy and speedy

---

### Post by DCJoeDog on 2006-03-21
BTW, taking the plunge now, will report on my misadventures LOL

---

### Post by nutrapi on 2006-03-21
though I'm new to the forums, I've been playing with ubuntu and various other linux distros for quite some time (back to mandrake 6 or so?).
I've recently used apt-get to upgrade and can say that it was relatively flawless other than my display properties. I had to re-run the xorg config(sudo dpkg-reconfigure xserver-xorg) but after that it's run great.

By far ubuntu has been the simplest yet most advanced distrobution I've ever used. "You decide your own level of involvement" - tyler (fight club)

I <3 ubuntu

~andrew

---

### Post by DCJoeDog on 2006-03-21
I get this error

```
After unpacking 416MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 115232 files and directories currently installed.)
Preparing to replace coreutils 5.2.1-2ubuntu2 (using .../coreutils_5.93-5ubuntu2_i386.deb) ...
Removing `local diversion of /usr/share/man/man1/md5sum.textutils.1.gz to /usr/share/man/man1/md5sum.1.gz'
dpkg-divert: rename involves overwriting `/usr/share/man/man1/md5sum.textutils.1.gz' with
  different file `/usr/share/man/man1/md5sum.1.gz', not allowed
dpkg: error processing /var/cache/apt/archives/coreutils_5.93-5ubuntu2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/coreutils_5.93-5ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

eep, help

---

### Post by mlind on 2006-03-21
[QUOTE=DCJoeDog]I get this error

```

Removing `local diversion of /usr/share/man/man1/md5sum.textutils.1.gz to /usr/share/man/man1/md5sum.1.gz'
dpkg-divert: rename involves overwriting `/usr/share/man/man1/md5sum.textutils.1.gz' with
  different file `/usr/share/man/man1/md5sum.1.gz', not allowed
dpkg: error processing /var/cache/apt/archives/coreutils_5.93-5ubuntu2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/coreutils_5.93-5ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
eep, help[/QUOTE]

*try removing /usr/share/man/man1/md5sum.1.gz manually, (make a backup first)
*try removing existing coreutils package first
*try to re-download coreutils package, remove it from /var/cache/apt/archives first

---

### Post by az on 2006-03-21
Your two helpful commands when untangling apt tangles when dealing with a developmental release:

sudo apt-get -f install (basically, fix it!)
sudo dpkg -- configure -a (fix everything!)

Keep trying those.  Throw in a dist-upgrade from time to time and it should work itself out.

---

### Post by DCJoeDog on 2006-03-21
in recovery mode as root(by default) I entered this

```
rm /usr/share/man/man1/md5sum.textutils.1.gz
rm /usr/bin/md5sum.textutils
sudo apt-get -f install
sudo dpkg -- configure -a
apt-get dist-upgrade
```

and THAT finally got it going again, so it seems all I had to do was "rm" those pesky files manulally

thanks for the help so far, back to the upgrade

---

### Post by DCJoeDog on 2006-03-21
I think I finished but when I login I get either a brown or grey screen and no keyboard control, but the pointer still moves via mouse input. hmmm

I think I am just gonna have to bite the bullet and just install via a cd, unless anyone else has an idea

---

### Post by it_self on 2006-03-21
The same happened to me upon trying to upgrade to breezy in a similar fashion. My only tip is to wait for update until after the new destribution has been out for at least a couple of weeks.

---

### Post by DCJoeDog on 2006-03-21
Oh well, after all that, I am back to where I began, except now I have separate partitions for /home and /usr

---

### Post by nutrapi on 2006-03-22
have you tried a -
sudo dpkg-reconfigure xserver-xorg
?
solved my grey screen/video issues to where I was then able to re-install the latest ati driver.

~andrew

---

### Post by ash211 on 2006-05-17
[QUOTE=DCJoeDog]I get this error

```
After unpacking 416MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 115232 files and directories currently installed.)
Preparing to replace coreutils 5.2.1-2ubuntu2 (using .../coreutils_5.93-5ubuntu2_i386.deb) ...
Removing `local diversion of /usr/share/man/man1/md5sum.textutils.1.gz to /usr/share/man/man1/md5sum.1.gz'
dpkg-divert: rename involves overwriting `/usr/share/man/man1/md5sum.textutils.1.gz' with
  different file `/usr/share/man/man1/md5sum.1.gz', not allowed
dpkg: error processing /var/cache/apt/archives/coreutils_5.93-5ubuntu2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/coreutils_5.93-5ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

eep, help[/QUOTE]

Just FYI for those who see this later, had this problem and fixed it with a 
```
sudo cp /usr/share/man/man1/md5sum.1.gz /usr/share/man/man1/md5sum.1.gz.bak
sudo rm /usr/share/man/man1/md5sum.1.gz
sudo apt-get dist-upgrade
```

---

### Post by G Morgan on 2006-05-20
I've just returned to Ubuntu and have to say that changing the sources.list and dist-upgrade worked perfectly. The only issue I had was it removed amarok which was solved in 20 seconds after reboot, also it closed Firefox (which I was using during the upgrade) when it installed 1.5 but 1.5 was working immeadiately so it was a simple reload.

I'm thinking of having a go at XGL next. Anyway I just thought I'd post to point out this worked well for me.

*after trying all and sundry in the last 2 months, I first started using Linux in the new year and after a few months with Ubuntu decided that Gentoo, Mepis and Fedora were worth a go in trying to expand my horizons.

---

### Post by siucdude on 2006-05-24
thank you this helped.:D 



[QUOTE=ash211]Just FYI for those who see this later, had this problem and fixed it with a 
```
sudo cp /usr/share/man/man1/md5sum.1.gz /usr/share/man/man1/md5sum.1.gz.bak
sudo rm /usr/share/man/man1/md5sum.1.gz
sudo apt-get dist-upgrade
```[/QUOTE]

---

### Post by mlind on 2006-05-24
[QUOTE=DCJoeDog]I get this error

```
After unpacking 416MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 115232 files and directories currently installed.)
Preparing to replace coreutils 5.2.1-2ubuntu2 (using .../coreutils_5.93-5ubuntu2_i386.deb) ...
Removing `local diversion of /usr/share/man/man1/md5sum.textutils.1.gz to /usr/share/man/man1/md5sum.1.gz'
dpkg-divert: rename involves overwriting `/usr/share/man/man1/md5sum.textutils.1.gz' with
  different file `/usr/share/man/man1/md5sum.1.gz', not allowed
dpkg: error processing /var/cache/apt/archives/coreutils_5.93-5ubuntu2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/coreutils_5.93-5ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

eep, help[/QUOTE]

backup file /usr/share/man/man1/md5sum.textutils.1.gz
and then remove it. Then try dist-upgrading.

---

### Post by sc0ty on 2006-05-24
After unpacking 244MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libxfixes3 libxcomposite1 libxss1 xserver-xorg-driver-i810 libdrm2 libglitz1
  libcairo2 libgl1-mesa-dri libgl1-mesa libglu1-mesa libtunepimp2c2a libsvg
  libsvg-cairo compiz
Install these packages without verification [y/N]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/sed_4.1.4-5_i386.deb (--unpack):
 files list file for package `libuuid1' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/sed_4.1.4-5_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


how can i solve this problem:
 files list file for package `libuuid1' is missing final newline
this appears in every installation i try to do in ubuntu =\

---

### Post by az on 2006-05-24
[QUOTE=sc0ty]


how can i solve this problem:
 files list file for package `libuuid1' is missing final newline
this appears in every installation i try to do in ubuntu =\[/QUOTE]


I think this is unrelated to a dist-upgrade - you have a corrupt package database.

sudo dpkg --clear-avail

should fix it.  Update and then dist-upgrade again.

---

### Post by nwgray on 2006-05-24
[QUOTE=dermotti]My dist-upgrade went flawless.....[/QUOTE]

My went like this:

graynw@ubuntu7:~/easyubuntu/easyubuntu$ sudo apt-get update
Get:1 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Fetched 5B in 1s (5B/s)
Reading package lists... Done
graynw@ubuntu7:~/easyubuntu/easyubuntu$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Apparently, I didn't find an update. What am I doing wrong but I don't know what. Thoughts? Help?

Thx

---

### Post by az on 2006-05-24
[QUOTE=nwgray]Apparently, I didn't find an update. What am I doing wrong but I don't know what. Thoughts? Help?

Thx[/QUOTE]
Change your sources to point to Dapper....

---

### Post by souteneur3190 on 2006-05-24
can u give me an example of that file?  i kno im doin sumthin wrong

---

### Post by richbarna on 2006-05-24
Type this in the terminal/console :-
> sudo gedit /etc/apt/sources.list
Then delete everything and copy and paste this :-
> 
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main 
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

I,ve already added the compiz repositories for your salivating over the 3D desktop etc.
Then :-
> sudo apt-get update
> sudo apt-get dist-upgrade

---

### Post by nwgray on 2006-05-25
[QUOTE=richbarna]Type this in the terminal/console :-

Then delete everything and copy and paste this :-

I,ve already added the compiz repositories for your salivating over the 3D desktop etc.
Then :-[/QUOTE]

That was it! Thx so much.

---

### Post by GarethMB on 2006-05-25
I've dist-upgraded numerous times, without a hitch.

---

### Post by richbarna on 2006-05-25
[QUOTE=nwgray]That was it! Thx so much.[/QUOTE]
No Biggie,
Have fun :)

---

