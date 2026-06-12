---
title: "Frustrated! Need help installing Flash"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by bvexen2 on 2006-08-27
Can someone please give me the easiest way to install Flash?  I tried for a couple hours yesterday with no luck.  Terminal is giving me this message:

robert@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
robert@ubuntu:~$

Can someone please help?

---

### Post by Bachstelze on 2006-08-27
Could you please paste your sources.list ? You seem to have a broken repo.

---

### Post by bvexen2 on 2006-08-27
sure, but I am not sure what that is or where I can get it....very new to ubuntu....

---

### Post by Bachstelze on 2006-08-27
open a terminal and run

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by bvexen2 on 2006-08-27
looks like you were right....this doesn't look good:

robert@ubuntu:~$ gksudo gedit /etc/apt/sources.list
(gedit:10189): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


what next?

---

### Post by Bachstelze on 2006-08-27
That doesn't look good indeed but in fact it's totally unimportant ;) gedit should have opened anyway with your file in it, paste it here.

---

### Post by nickpaton on 2006-08-27
Open your Terminal.

Copy the following, and paste it into the Terminal after :~$ prompt:

```
sudo gedit /etc/apt/sources.list
```

This will open up a new window sources.list.

Copy the contents of it, click on the # above the posting window, and paste the contents between the ```
 
``` icons into your reply.

Post the reply.

Close the sources.list window.

*Well beaten to the post!*

---

### Post by bvexen2 on 2006-08-27
below is from sources.list

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## created by arnielistenremoved

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) breezy main

---

### Post by Bachstelze on 2006-08-27
nickpaton, please have a look at [this](https://help.ubuntu.com/community/RootSudo).

> 
**NEVER** use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail. If this happens and at login an error message reports: "Unable to read ICE authority file", log in using the failsafe terminal and execute the command below substituting user for your username.

---

### Post by nickpaton on 2006-08-27
> **HymnToLife said:**
> That doesn't look good indeed but in fact it's totally unimportant ;) gedit should have opened anyway with your file in it, paste it here.

@hymn to Life: I tried the gksudo etc command and also got the same error message, but then the sources.list opened up.

I then tried straight sudo etc, and it opened sources.list straight away.

Weird as you say.

@bvexen: try the command with sudo instead of gksudo.

---

### Post by Bachstelze on 2006-08-27
**bvexen2**, I stongly recommend you update to Dapper. Delete everything in your ources.list, copy/paste [this](http://paste.ubuntu-nl.org/6666) instead then save, close gedit and run

```

sudo apt-get update
sudo apt-get dist-upgrade
```

**nickpaton**, I get it too but better get a harmless eroor message than mess your whole paermisions sytem up I reckon...

---

### Post by nickpaton on 2006-08-27
> **HymnToLife said:**
> nickpaton, please have a look at [this](https://help.ubuntu.com/community/RootSudo).

Many thanks for the advise - this is what I like about the forums here.
Learnt something new.

---

### Post by bvexen2 on 2006-08-27
from sources.list using sudo:

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## created by arnielistenremoved

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) breezy main

---

### Post by Bachstelze on 2006-08-27
Using sudo or gksudo won't change the contents of the file ;)

---

### Post by bvexen2 on 2006-08-27
hymntolife - I did update to Dapper and ran the code and Terminal ended with this:

923 upgraded, 194 newly installed, 43 to remove and 0 not upgraded.
Need to get 526MB of archives.
After unpacking 338MB of additional disk space will be used.
Do you want to continue [Y/n]?

Do I need to continue?  I assume so.

Also, a popup came up on my PC and said New Updates are available???

---

### Post by Bachstelze on 2006-08-27
Yep, you continue :) I hope you have a fast connection, with 526 MB to download...

---

### Post by mindtrick on 2006-08-27
I'm a newbie too. I thought easyubuntu thing installs flash automatically, doesn't it? I'm currently installing dapper so i have no experience about it, i'm planning to make it with easyubuntu.

---

### Post by Bachstelze on 2006-08-27
It's supposed to but I prefer not to use this kind of tools and do it all myself.

---

### Post by bvexen2 on 2006-08-27
its running right now....thanks for your help.  is this the last step?  will flash be installed now?

The site I am having trouble viewing says I need the lastest Flash from Adobe Systems....is that what we are doing here?

what is easyubuntu?

---

### Post by Bachstelze on 2006-08-27
Nope, we are upgrading your sytem to Dapper Drake, which is the latest Ubuntu release. To get Flash after that, run (for Firefox) :

```
sudo apt-get install flashplugin-nonfree
```

esyubuntu is a script that automates installation of a few basic things (codecs, Flash, Java...). Use it if you want but personnaly, I don't like this kind of tools.

---

### Post by bvexen2 on 2006-08-27
Great, thanks, I'll let you know what happens after I run that coding.  It is at 48% right now.....

---

### Post by bvexen2 on 2006-08-27
hymntolife:  what do I do here?

Configuration file `/etc/login.defs'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** login.defs (Y/I/N/O/D/Z) [default=N] ?

---

### Post by Bachstelze on 2006-08-27
Stick with the defaults I think. If your file is different, it's for a reason.

---

