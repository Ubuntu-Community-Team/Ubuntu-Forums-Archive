---
title: "Adept problems"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Jezza on 2006-07-07
I'd like to install Firefox and the consensus seems to be that Adept is the way to go - I'm using Kubuntu 6.06. When I start Adept up comes a long list of programs, including Firefox (and Thunderbird, which I also want). In the status field next to Firefox it says Installed. In fact every program's field says installed next to it. 

When I click on the program name I get the option for Request Removal, or Details. Neither seem to do anything, and I get no option to install. When I go to fetch updates it tells me it is waiting for headers and doesn't do anything. Is Firefox installed by default, and if so, where is it and how do I run it? 

I'd like to somehow check for security updates as well, but Adept doesn't seem to give me any option to do so. When I untick the box that lists Installed, leaving just Not Installed ticked, there are no options listed. 

What's going on? Where am I going wrong with installing stuff?

---

### Post by T700 on 2006-07-07
I'm not at a Linux box right now, so I can't walk you through it, but there are filters in place.  Look up top of the Adept screen and see if there are boxes to tick and untick that control if you will see only installed, only uninstalled, and other groupings of programs.

Paul

---

### Post by richbarna on 2006-07-07
> **Jezza said:**
> I'd like to install Firefox and the consensus seems to be that Adept is the way to go - I'm using Kubuntu 6.06. When I start Adept up comes a long list of programs, including Firefox (and Thunderbird, which I also want). In the status field next to Firefox it says Installed. In fact every program's field says installed next to it. 

When I click on the program name I get the option for Request Removal, or Details. Neither seem to do anything, and I get no option to install. When I go to fetch updates it tells me it is waiting for headers and doesn't do anything. Is Firefox installed by default, and if so, where is it and how do I run it? 

I'd like to somehow check for security updates as well, but Adept doesn't seem to give me any option to do so. When I untick the box that lists Installed, leaving just Not Installed ticked, there are no options listed. 

What's going on? Where am I going wrong with installing stuff?

T700 is right. When you do an Adept search you have the options for it to show Installed/ Not Installed/Upgradable. Find these boxes and check all of them. Take a look at this image :-
[http://photos1.blogger.com/blogger/2810/2009/1600/Adept.png](http://photos1.blogger.com/blogger/2810/2009/1600/Adept.png)

If you have something installed, it should be on the programs menu list.
To check if a program is installed but not on the list, you can press Alt + F2 and a run box will open, type firefox and press enter.

---

### Post by Jezza on 2006-07-07
I've found the boxes alright. With all of them ticked there is a long list, and everything says it is installed, including Firefox. When I do Alt+F2 and type Firefox it says "Could not run the specified command". 

I would reckon that I need to tick Not Installed together with Install to get a list of things I don't have and that I want it to get them. But when I do that nothing shows in the list at all, and if I click fetch updates it just says waiting for headers. In fact the only option that lists anything is Installed together with No Changes, or if all boxes are ticked. That says everything's status is installed. But I can't run anything on the list using that Alt+F2 command.

---

### Post by richbarna on 2006-07-07
hmm, it's a bit of a poser, try :-
> sudo apt-get update && sudo apt-get upgrade

Then tell us if you get any problems. It maybe a sources list problem.
I expect you already know this, but don't leave Adept open while you are connecting through the Konsole, or you will get an error can't connect message.

---

### Post by Jezza on 2006-07-07
No luck, unfortunately. My connection is pretty good as a rule - 1MB ADSL through a router, but it sat there for ages on 0% then came up with this: 

Errhttp://packages.freecontrib.org dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed o                                          ut
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release).                                          gpg  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection time                                          d out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used                                           instead.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aero@aero-desktop:~$

---

### Post by richbarna on 2006-07-07
ok, do this in your konsole :-
> kdesu kate /etc/apt/sources.list

Find the deb  [http://packages.freecontrib.org/ubun...dapper/Release]("http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release")
and put a comment in front of it, (this #). Click Save and Exit.

Maybe you could post a copy of the sources list just in case there's a problem with it.

Then do the previous commands from my other post to update again.

---

### Post by Jezza on 2006-07-07
This is the sources list:

> # deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free 
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted 
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted 
## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe 
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe 
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

I tried the apt-get command and it spewed up a load of error messages:

> aero@aero-desktop:~$ kdesu kate /etc/apt/sources.list
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
ScimInputContextPlugin()
kate: WARNING: Can't open /root/share/apps/konqueror/bookmarks.xml
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
sudo apt-get update && sudo apt-get upgrade

I'm guessing input device 166 is the router which is somehow timing out, but I'm pretty much in the dark about this stuff - I just plugged it in before the install and it kind of work.

---

### Post by infoseeker on 2006-07-07
This is my sources.list file. Why are all your lines hashed out (iow disabled) ?

Just change the 'za' to 'gb' for your area (i'm in S Africa :) ).

> # Specialized Basic Ubuntu Multimedia Preparation Script sources.

# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ dapper main restricted

## Uncomment the following two lines to fetch updated software from the network

deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.

deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe' repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

## PLF repo's.
# deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
# deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free


and to edit your 'sources.list' file while in Gnome (Ubuntu) use
> gksu gedit /etc/apt/sources.list
or
> kdesu kate /etc/apt/sources.list
for Kubuntu (KDE)

Good Luck !

---

### Post by richbarna on 2006-07-07
Exactly what Jezza said, you haven't got any repositories enabled.
So do the commands that he said to edit the sources list, then instead of editing, just delete all of it and copy and paste this:-
> 
##Ultimate Dapper Sources List

##Standard Ubuntu Packages
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

## Automatix (PGP Key: 521A9C7C)

##deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

##Wine

##deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
##deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

##Seveas Packages Not Included In Ubuntu

##deb [http://users.lichtsnel.nl/~seveas]("http://users.lichtsnel.nl/%7Eseveas") dapper-seveas extras
##deb-src [http://users.lichtsnel.nl/~seveas]("http://users.lichtsnel.nl/%7Eseveas") dapper-seveas extras

##Cipherfunk multimedia packages (PGP key: 33BAC1B3)

##deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
##deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

##Dapper PLF

##deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
##deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free







 Then do :-
> sudo apt-get update && sudo apt-get upgrade 
That should sort out your adept problem. :)

---

### Post by Jezza on 2006-07-08
It all looked so promising... I followed every step in the post above, pasted the new sources list into Kate and saved it, so it looked like this:

> ##Ultimate Dapper Sources List
 
 ##Standard Ubuntu Packages
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
 deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
 
 deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
 deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
 
 ## Automatix (PGP Key: 521A9C7C)
 
 ##deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main
 
 ##Wine
 
 ##deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
 ##deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
 
 ##Seveas Packages Not Included In Ubuntu
 
 ##deb [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas extras
 ##deb-src [http://users.lichtsnel.nl/~seveas](http://users.lichtsnel.nl/~seveas) dapper-seveas extras
 
 ##Cipherfunk multimedia packages (PGP key: 33BAC1B3)
 
 ##deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
 ##deb-src [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main
 
 ##Dapper PLF
 
 ##deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
 ##deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
 
 


Then did:
> sudo apt-get update && sudo apt-get upgrade

...but came up against the same problem:

> Errhttp://packages.freecontrib.org dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aero@aero-desktop:~$                                                 

---

