---
title: "text editor for kubuntu"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Learn!ng on 2008-01-09
just got gutsy just now... 

Hello 

kate and open office are not my preferred text editors... just need to do some rich text editing... fonts italics... is there any other alternatives?

also is there any way to get a package in a self extrating form rather than a pseudo download... so if i need to reformat then i don't need inet access to get it running again?

---

### Post by LaRoza on 2008-01-09
You can use Abiword, it is a word processor, but it is lighter and faster. It has less features than OO.

---

### Post by Learn!ng on 2008-01-09
ok how to get it tho?

---

### Post by PmDematagoda on 2008-01-09
You can install it using:-
```
sudo apt-get install abiword
```

---

### Post by Learn!ng on 2008-01-09
ok tried but app not in the repository

---

### Post by PmDematagoda on 2008-01-09
Open Software Sources in System>Administration>Software Sources and enable all the Ubuntu Software repositories, reload the sources list as requested when closing the window and try installing Abiword again.

---

### Post by sumguy231 on 2008-01-09
> Open Software Sources in System>Administration>Software Sources and enable all the Ubuntu Software repositories, reload the sources list as requested when closing the window and try installing Abiword again.
Or you can do that from Adept Manager (K -> System -> Adept Manager) if you don't have Gnome.

---

### Post by Learn!ng on 2008-01-09
ok well i went away and tried a few things...

and i am not really sure what i am doing in adept manager at the moment...

the thing is I noticed in the gutsy packages the wine already seems to be installed in the add/remove --> settings section

however then i tried to load on some windows apps, but nothing happen with the windows exe files....

so do i need to do something with the adept manager to get access to more apps from sudo... 

or is it better to get wine working properly and what do i need to do in either case?

---

### Post by Learn!ng on 2008-01-09
also is there an alternative to cron jobs?  like a scheduler replacement for it, or is it part of the core linux kernel?

---

### Post by Learn!ng on 2008-01-09
oh yeah... and what is the difference between sudo and the wget statements

on my pc the wget seems to work not the sudo?

---

### Post by PmDematagoda on 2008-01-09
You can run a .exe file using:-
```
wine nameoffile.exe
```
or by right-clicking on the file and selecting Open with Wine.

You can configure Wine by executing:-
```
winecfg
```

You may also use [Wine-doors]("http://www.wine-doors.org/wordpress/?page_id=3") which is an application made to simplify Wine.

---

### Post by Learn!ng on 2008-01-09
ah ok...

i tried the right click and open with

but it seems like it isn't installed for right click menus with gutsy?


and i tried winecfg in terminal but nothing happened either?

but it is there in the add/remove section?:confused:

---

### Post by Learn!ng on 2008-01-09
You may also use [Wine-doors]("http://www.wine-doors.org/wordpress/?page_id=3") which is an application made to simplify Wine.[/QUOTE]

i tried downloading a tarball before... but someone here gave me a wget statement instead.. so not really sure if i need it or not???

---

### Post by Learn!ng on 2008-01-09
ok... got the tarball... what to do to make it a proper road?

---

### Post by PmDematagoda on 2008-01-09
Why are you trying to get the tarball when there is a .deb installer of it for Ubuntu?

---

### Post by Learn!ng on 2008-01-09
well i clicked the deb/ubuntu link and nada... tried the tarball and down it came.

---

### Post by PmDematagoda on 2008-01-09
Are you sure that you cannot download the .deb? I can download the file properly. Wait a little after clicking the link.

---

### Post by Learn!ng on 2008-01-09
ok now i have both tarball and deb file on my desktop... what's next?

---

### Post by PmDematagoda on 2008-01-09
Just double-click the .deb file, that should start the install process. You can get rid of the tarball.

---

### Post by Learn!ng on 2008-01-09
clicked on the tarball and can move around... but what to click on?

the deb file fell over: dependency not satisfied?

---

### Post by PmDematagoda on 2008-01-09
Post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by Learn!ng on 2008-01-09
ok but there lots...

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main
restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted unive
rse multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted u                                          niverse multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
tehhulk@tehhulk-desktop:~$
tehhulk@tehhulk-desktop:~$

---

### Post by PmDematagoda on 2008-01-09
Open the sources.list file for editing using:-
```
kdesu kate /etc/apt/sources.list
```

Then remove the # in front of the repository addresses so that lines such as these:-
```
**[COLOR="Red"]#[/COLOR]**deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted

[COLOR="Red"]**#**[/COLOR]deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
```
will look like this:-
```
deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted

deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
```

After the editing is done, save the file and then execute:-
```
sudo apt-get update
```
after that is completed you should be able to install Wine-doors properly.

---

### Post by Learn!ng on 2008-01-09
ya well thats where i have a problem... i removed the text editing apps and now i can't get them reinstalled either... 

so i can't edit or view any files at the moment with gutsy!

---

### Post by PmDematagoda on 2008-01-09
Well, then you will have to use a CLI text-editor or go to Adept and Settings and Repository settings and enable all, that should work as well.

---

### Post by Learn!ng on 2008-01-09
i did just download opera with a wget statement and that did work tho...

---

### Post by PmDematagoda on 2008-01-09
Yes, WGet works since it does not concern the repositories, but package managers will not work.

---

### Post by Learn!ng on 2008-01-09
in adept manager... no option to:

 Settings and Repository settings and enable all

there is

adept--> manage repositories  and fetch updates.. but they don't seem to do much?

---

### Post by PmDematagoda on 2008-01-09
Try Manage Repositories.

---

### Post by adityakavoor on 2008-01-09
wget is a download manager

```
man wget
```

sudo is used to get root access

```
man sudo
```

---

### Post by vikram on 2008-01-09
try Kword a KDE based text editor

review here [http://itmanagement.earthweb.com/osrc/article.php/3715536](http://itmanagement.earthweb.com/osrc/article.php/3715536)

sudo apt-get install kword

or

use adept manager and install Kword. SInce you already have KDE it should be in the repos.

---

### Post by Learn!ng on 2008-01-09
ok so now if i need to get wine where do i look to create the wget statement?

---

### Post by PmDematagoda on 2008-01-09
Learn!ng you are trying to fix the solution the hard way, please follow the advice I gave and  activate the repositories and use them, otherwise you may not be able to satisfy Wine-door's dependencies and you will face problems installing other applications as well.

---

### Post by Learn!ng on 2008-01-09
> **vikram said:**
> try Kword a KDE based text editor

review here [http://itmanagement.earthweb.com/osrc/article.php/3715536](http://itmanagement.earthweb.com/osrc/article.php/3715536)

sudo apt-get install kword

or

use adept manager and install Kword. SInce you already have KDE it should be in the repos.

i still have probs with sudo ...

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package kword

and struggling with adept too... and i can't see it in the adept manager list either

---

### Post by PmDematagoda on 2008-01-09
Learn!ng, please understand, the repositories contain all the software that you want to install on your OS, the reason you do not see a list in Adept and you cannot install anything using apt-get is because your repositories are disabled, your problems can be fixed if you simply enable the repositories.

---

### Post by Learn!ng on 2008-01-09
> **PmDematagoda said:**
> Learn!ng you are trying to fix the solution the hard way, please follow the advice I gave and  activate the repositories and use them, otherwise you may not be able to satisfy Wine-door's dependencies and you will face problems installing other applications as well.

ok sure...

kword would be a quick fix for me

but wine is an option too...

---

### Post by Learn!ng on 2008-01-09
> **PmDematagoda said:**
> Learn!ng, please understand, the repositories contain all the software that you want to install on your OS, the reason you do not see a list in Adept and you cannot install anything using apt-get is because your repositories are disabled, your problems can be fixed if you simply enable the repositories.


ok... how to enable repositories...?

---

### Post by lespaul_rentals on 2008-01-09
Did you remove the # characters from the restricted lines in /etc/apt/sources.list yet?

Please do the following, you can use Kate or Kwrite, both of which should be installed by default.  You need to do this before you can move on.

> **PmDematagoda said:**
> Open the sources.list file for editing using:-
```
kdesu kate /etc/apt/sources.list
```

Then remove the # in front of the repository addresses so that lines such as these:-
```
**[COLOR="Red"]#[/COLOR]**deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted

[COLOR="Red"]**#**[/COLOR]deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
```
will look like this:-
```
deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted

deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
```

After the editing is done, save the file and then execute:-
```
sudo apt-get update
```
after that is completed you should be able to install Wine-doors properly.

---

### Post by PmDematagoda on 2008-01-09
Did you try the Manage Repositories option in Adept?

---

### Post by Learn!ng on 2008-01-09
> **PmDematagoda said:**
> Did you try the Manage Repositories option in Adept?


i am looking at that section at the moment... which tab do i need

i have kubuntu.... third party ...updates..authentication.. stats?

---

### Post by PmDematagoda on 2008-01-09
Enable all the check boxes except the one for the CD-ROM in the Kubuntu tab for now.

EDIT:- Also enable all the check boxes except for the Pre-released Updates in the Updates tab.

---

### Post by Learn!ng on 2008-01-09
> **lespaul_rentals said:**
> Did you remove the # characters from the restricted lines in /etc/apt/sources.list yet?

Please do the following, you can use Kate or Kwrite, both of which should be installed by default.  You need to do this before you can move on.

i removed them already tho... and now i need a new app maybe a wget for kword?

---

### Post by Learn!ng on 2008-01-09
> **PmDematagoda said:**
> Enable all the check boxes except the one for the CD-ROM in the Kubuntu tab for now.

its is the kubuntu software tab.. and there is no cd rom option.

---

### Post by Learn!ng on 2008-01-09
ok i think i got it,,, just abt finished downloading what next :)

---

### Post by PmDematagoda on 2008-01-09
Did the sources list reload finish?

---

### Post by Learn!ng on 2008-01-09
i can see kword is there in the manager now... how to get at it??? sudo or wget?

---

### Post by PmDematagoda on 2008-01-09
Use:-
```
sudo apt-get install kword
```
But you may disregard my previous instructions since you have successfully enabled your repositories, Wine-doors should now be able to install properly.

---

### Post by Learn!ng on 2008-01-09
> **PmDematagoda said:**
> Use:-
```
sudo apt-get install kword
```
But you may disregard my previous instructions since you have successfully enabled your repositories, Wine-doors should now be able to install properly.

awsum... unpacking now!

i think it is bed for me 4:44 am! thks again!

---

### Post by PmDematagoda on 2008-01-09
Glad to have been able to help:).

---

