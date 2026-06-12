---
title: "[SOLVED] Java problems"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by LostMagix on 2007-12-06
E: The package sun-java5-bin needs to be reinstalled, but I can't find an archive for it.


im a noob what do i do

---

### Post by erfahren on 2007-12-06
could you provide more information? what version of Ubuntu? what were you trying to run when you got that error? have you installed any version of java? If you just installed Ubuntu were you able to get updates?

---

### Post by Hospadar on 2007-12-06
when do you get this error, and does java work for you?

Also could you run (from a terminal) ```
sudo update-alternatives --config java
``` and copy the dialog to this forum

Also post the output of "java --version"

And could you check you System->Administration->Software Sourcres and make sure "Installable from cd" is _not_ chekced.

---

### Post by OldTimeTech on 2007-12-06
you might try going to system->administration->synaptic package manager after opening that click on search and type in sun-java5-bin....it should give you what you are looking for and probably much more.

Also make sure you have all repositories checked so that sun-java5-bin can be found.

---

### Post by LostMagix on 2007-12-06
ubuntu 7.10 gutsy

kernel linux 2.6.22-14-generic

gnome 2.20.1

i just got ubuntu 2 days ago and i was trying to install java (to run frostwire) on the install window for frostwire it said i need to install sun-java5-bin so i put in "sudo apt-get install sun-java5-bin"

i ran it and now it keeps saying......

"E: The package sun-java5-bin needs to be reinstalled, but I can't find an archive for it."

when ever i try to run a java app or try to install java off the web site

any idea what to do? i would appreciate it

---

### Post by rsambuca on 2007-12-06
You have to enable your multiverse repositories.  System - Administration - Software Sources.   Make sure the multiverse box is checked.  You will then be able to install the java.

---

### Post by LostMagix on 2007-12-06
> **Hospadar said:**
> when do you get this error, and does java work for you?

Also could you run (from a terminal) ```
sudo update-alternatives --config java
``` and copy the dialog to this forum

Also post the output of "java --version"

And could you check you System->Administration->Software Sourcres and make sure "Installable from cd" is _not_ chekced.

it gives me a update prompt the the same window

"E: The package sun-java5-bin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

and for the other suggestion you gave me i got this

"There is only 1 program which provides java
(/usr/bin/gij-4.2). Nothing to configure."

---

### Post by LostMagix on 2007-12-06
> **OldTimeTech said:**
> you might try going to system->administration->synaptic package manager after opening that click on search and type in sun-java5-bin....it should give you what you are looking for and probably much more.

Also make sure you have all repositories checked so that sun-java5-bin can be found.

i did do a few hours of research before i came here and i saw that, but then i run the synaptic package manager i get the same "sun-java5-bin needs to be reinstalled" error message

---

### Post by OldTimeTech on 2007-12-06
And all of your repositories are checked???

---

### Post by LostMagix on 2007-12-06
> **OldTimeTech said:**
> And all of your repositories are checked???

yep

---

### Post by rsambuca on 2007-12-06
Then your repos are messed up.  Post the output of 

cat /etc/apt/sources.list

---

### Post by OldTimeTech on 2007-12-06
again in synaptic....down at the bottom click on custom filters....it shows broken, update and bunch of others....check in broken for the sun-java5-bin...if it's there right click your mouse on it and see what options it offers to fix broken....should offer re-install or fix...try that

---

### Post by LostMagix on 2007-12-06
the whole sha-bang




# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main restricted multiverse #Added by software-properties
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by LostMagix on 2007-12-06
> **OldTimeTech said:**
> again in synaptic....down at the bottom click on custom filters....it shows broken, update and bunch of others....check in broken for the sun-java5-bin...if it's there right click your mouse on it and see what options it offers to fix broken....should offer re-install or fix...try that

i cant open it, i just get the same error

---

### Post by OldTimeTech on 2007-12-06
I agree with rsambuca....somehow your list doesn't look right....it looks like nothing is updating.

This is what mine looks like...please ignore the fact I use automatix....LOL

marianne@rebelwoman:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security multiverse


#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
#AUTOMATIX REPOS END

---

### Post by LostMagix on 2007-12-06
i ran the updater when i installed ubuntu............

so what would you suggest, i cant run updates due to that pesky little error

well this is still better then vista.....

---

### Post by OldTimeTech on 2007-12-06
Well you could back up your sources.lst and then copy mine and see if you get the same error.

---

### Post by LostMagix on 2007-12-06
> **OldTimeTech said:**
> Well you could back up your sources.lst and then copy mine and see if you get the same error.

im sorry you will have to excuse me, like i said im noob at this, if you could explain how to do that.......

not backing it up, but how copy your into it

---

### Post by erfahren on 2007-12-06
@LostMagix
you might want to clean up your sources.list

back up your current one:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_back

```
(Edited in #-o ) open up your current sources.list 
```

gksudo gedit /etc/apt/sources.list

```
replace everything in there with:
```

## CD-ROM
## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Uncomment deb-src if you wish to download the source packages

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse 
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted 
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted 
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted 

## START -- MANUALLY ADDED
##

## CANONICAL REPOSITORY
deb http://archive.canonical.com/ubuntu gutsy partner

## BACKPORTS REPOSITORY
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse

## THIRD-PARTY REPOSITORIES
##
## MEDIBUNTU  
deb http://packages.medibuntu.org/ gutsy free non-free

```
add the key for Mediubuntu and update
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```
You should be able to find Java then.

Note: Java 6 update 3 is available in Gutsy repositories.  just run: 
```

sudo aptitide install sun-java6-plugin

```
and you should get everything you need.

---

### Post by OldTimeTech on 2007-12-06
Do like erfahren says and shows you....

his is a ++ system ;)

---

### Post by LostMagix on 2007-12-06
how do i replace that though??

---

### Post by erfahren on 2007-12-06
copy the sources.list from my post, and then highlight everything in your sources.list that you have open in gedit ( Edit > Select All -or- Ctrl+A) and paste.

---

### Post by rsambuca on 2007-12-06
> **LostMagix said:**
> how do i replace that though??

After you have copied it, you need to open it in a text editor, which is called gedit.  The command gksudo gives you the required permissions to access the file.```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Irony on 2007-12-06
In terminal (accessories > terminal) type;

```
gksudo gedit /etc/apt/sources.list
```

Then copy and paste the previously mentioned contents in to it, save it close it.

Then go to synaptic, hit the reload button - then type java in the search bar then install which ever one you want (just try one of them).

---

### Post by LostMagix on 2007-12-06
> **erfahren said:**
> copy the sources.list from my post, and then highlight everything in your sources.list that you have open in gedit ( Edit > Select All -or- Ctrl+A) and paste.

what program are you useing for this, im useing the terminal and i dont see anything like that

---

### Post by LostMagix on 2007-12-06
```
chris@chris-desktop:~$ cat /etc/apt/sources.list
## CD-ROM
## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Uncomment deb-src if you wish to download the source packages

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse 
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted 
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted 
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted 

## START -- MANUALLY ADDED
##

## CANONICAL REPOSITORY
deb http://archive.canonical.com/ubuntu gutsy partner

## BACKPORTS REPOSITORY
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-backports universe multiverse

## THIRD-PARTY REPOSITORIES
##
## MEDIBUNTU  
deb http://packages.medibuntu.org/ gutsy free non-fre
chris@chris-desktop:~$ 

```


thats what i came out with, no luck, same problem

---

### Post by rsambuca on 2007-12-06
Remove the CD line from your repositories.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

---

### Post by LostMagix on 2007-12-06
nope :(

---

### Post by rsambuca on 2007-12-06
Run the following commands in order, and see if any error messages pop up.```
sudo apt-get update && sudo apt-get upgrade
```
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by erfahren on 2007-12-06
@LostMagix
when you do
```

gksudo gedit /etc/apt/sources.list

```
that opens your sources.list in the text editor {gedit) with root permissions so you can edit it.

**NOTE: I just realized I forgot that part in my previous post. oops, Sry!**
I'll go back and fix it.

Sorry, LostMagix, "my bad"!

---

### Post by LostMagix on 2007-12-06
```

.....
...
....
W: GPG error: http://packages.medibuntu.org gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

```
chris@chris-desktop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java5-bin: Depends: sun-java5-jre (= 1.5.0-13-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
chris@chris-desktop:~$ 
```

---

### Post by LostMagix on 2007-12-06
new message for synaptic now

```
You have 1 broken package on your system!

Use the "Broken" filter to locate it.
```

but its running

---

### Post by rsambuca on 2007-12-06
First, correct your Sources.list.  It looks like you are missing the last 'e' from the word non-free in the last line.

Second, run the command```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Third run this command```
sudo apt-get -f install
```

---

### Post by LostMagix on 2007-12-06
> **rsambuca said:**
> First, correct your Sources.list.  It looks like you are missing the last 'e' from the word non-free in the last line.

Second, run the command```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Third run this command```
sudo apt-get -f install
```

same on both

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

i also just tryed frostwire again,this time i got

Error:failed to satisfy all dependencies (broken cache)

as status

---

### Post by rsambuca on 2007-12-06
> **LostMagix said:**
> same on both

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

i also just tryed frostwire again,this time i got

Error:failed to satisfy all dependencies (broken cache)

as status

Before trying a bunch of different things.  Please just stop and read what the error messages are telling you.  Close your Synaptic Package Manager.  Then run the 'sudo apt-get -f install' command

Did you correct your sources.list?
Did you add the medibuntu key?

---

### Post by LostMagix on 2007-12-06
```
chris@chris-desktop:~$ sudo apt-get -f install
[sudo] password for chris:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chris@chris-desktop:~$ 


```

that is what i get

---

### Post by rsambuca on 2007-12-06
Close everything first.  Close Synaptic.  Close your Add/Remove Programs...

---

### Post by LostMagix on 2007-12-06
k i just did a reboot and this is what i got

```
chris@chris-desktop:~$ sudo apt-get -f install
[sudo] password for chris:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
chris@chris-desktop:~$ 
```

i also got a upgrade prompt on startup, did have one last time, long list to

run it?

---

### Post by rsambuca on 2007-12-06
sudo dpkg --configure -a

---

### Post by LostMagix on 2007-12-06
```
chris@chris-desktop:~$ sudo dpkg --configure -a
chris@chris-desktop:~$ 

```

no error...

---

### Post by rsambuca on 2007-12-06
Now try the sudo apt-get -f install again.

---

### Post by LostMagix on 2007-12-06
```
chris@chris-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  sun-java5-bin sun-java5-jre
Suggested packages:
  sun-java5-plugin ia32-sun-java5-plugin sun-java5-fonts
The following packages will be upgraded:
  sun-java5-bin sun-java5-jre
2 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
2 not fully installed or removed.
Need to get 0B/29.9MB of archives.
After unpacking 83.5MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

after that i did see a error, not sure what it said though, it went straight to this

```
Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java5-bin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;  
 &#9474;     form, any other machine readable materials including, but not         &#9618;  
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                              
```

---

### Post by rsambuca on 2007-12-06
Good!  It is working!  Now read the user agreement, and use the arrow keys to get to the bottom of the agreement.  click OK (I think you use the tab key).  Then you should be good to go.

---

### Post by LostMagix on 2007-12-06
you know what, i think im just gonna reinstall ubuntu, seems a lot easer

---

### Post by rsambuca on 2007-12-06
WHY?  It is fixed now!

---

### Post by LostMagix on 2007-12-06
lolz never mind i think this is it
```

chris@chris-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  sun-java5-bin sun-java5-jre
Suggested packages:
  sun-java5-plugin ia32-sun-java5-plugin sun-java5-fonts
The following packages will be upgraded:
  sun-java5-bin sun-java5-jre
2 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
2 not fully installed or removed.
Need to get 0B/29.9MB of archives.
After unpacking 83.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java5-bin' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `sun-java5-jre' missing, assuming package has no files currently installed.
89207 files and directories currently installed.)
Preparing to replace sun-java5-bin 1.5.0-13-0ubuntu1 (using .../sun-java5-bin_1.5.0-13-0ubuntu1_i386.deb) ...
Unpacking replacement sun-java5-bin ...
Preparing to replace sun-java5-jre 1.5.0-13-0ubuntu1 (using .../sun-java5-jre_1.5.0-13-0ubuntu1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java5-jre ...
Setting up sun-java5-bin (1.5.0-13-0ubuntu1) ...
No theme index file in '/usr/share/icons/sun-java5.png'.
If you really want to create an icon cache here, use --ignore-theme-index.

Setting up sun-java5-jre (1.5.0-13-0ubuntu1) ...

chris@chris-desktop:~$ 

```

look about right?

---

### Post by rsambuca on 2007-12-06
Yup.

If you just reinstall now after all of this, I may have to hunt you down...

---

### Post by LostMagix on 2007-12-06
ZOMG ITS WORKING

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

THANK YOU

YOUR THE BEST!!!! ^_^v

---

### Post by erfahren on 2007-12-06
good to hear! I really apologize for forgetting that part in my post before and messing you up! 

but you learned a little something today, didn't you? (at least that's what I'm telling myself to feel better - lol !)

anyway, you can mark this thread as "Solved" by going to the "Thread Tools" above the first post.

good luck!

---

