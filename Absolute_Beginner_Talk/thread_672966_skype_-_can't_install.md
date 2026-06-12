---
title: "skype - can't install"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by betsy_kevin on 2008-01-20
Hiya everyone-
My linux project is up and running - thanks everyone - Now I'm trying to install skype, after I download the package and double click to install it, I get a message:


Error: Dependency is not satisfiable: libq4-core


Boy, I dont want that..how do I satisfy my core and load skype (donuts?)

Thanks!!

---

### Post by njparton on 2008-01-20
Tty installing that dependancy first:

```
sudo apt-get install libq4-core
```

I always use automatix to install stuff like this in ubuntu and it works a charm.  Google it to see if there's a version available for mint.

---

### Post by xtrm_redbull on 2008-01-20
Or you could add the [medibuntu repository]("https://help.ubuntu.com/community/Medibuntu") and install skype 2.0.0.27, google earth and [alot more]("http://www.medibuntu.org/packages.php"), from synaptic package manager. :)

---

### Post by Lisa Y on 2008-01-20
hello....im a total noob at ubuntu as well...but ive searched and ....SEARCHED lol and i finally...(almost there) figured out how to use ubuntu...

.When you get those..."Error Dependency" it just means that the program you are trying to install needed an dependency for it to install. So heres how you can install skype...

```
sudo apt-get install libq4-core 
```

if that fails...then install the file manually which is here

[http://packages.ubuntu.com/gutsy/libs/libqt4-core](http://packages.ubuntu.com/gutsy/libs/libqt4-core)

just pick which is your pack..and download....

---

### Post by billgoldberg on 2008-01-20
Adding the medibuntu repository would be better. Synaptic will then download and install all dependencies for you and will let you update the program using the update manager.

Go to synaptic package manger (system-> administration). Then in synaptic, go to setting -> repositories. Tne go to the "third party software" tab and press add.

Paste this line:

 deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free 

Then in synaptic press the reload button.

And search for skype.

---

### Post by betsy_kevin on 2008-01-21
**Boy I'm really getting lost trying to install Skype. Trying the first suggestion I get the message:**

Reading package lists... Done

Building dependency tree       

Reading state information... Done

E: Couldn't find package libq4-core


**Trying the second suggestion**, 

Adding the medibuntu repository would be better. Synaptic will then download and install all dependencies for you and will let you update the program using the update manager.

Go to synaptic package manger (system-> administration). Then in synaptic, go to setting -> repositories. Tne go to the "third party software" tab and press add.

Paste this line:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Then in synaptic press the reload button.

**I get a weird message**:

Enter the complete APT line of the repository that you want to add as source
he APT line includes the type, location and components of a repository, for example  'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main'.
[B]

with a blank line that I guess that I have to type a path[/B]

[B]
HELP!!!!!!!!!!![/B] Am I in over my head with this stuff???

---

### Post by plucky on 2008-01-21
To add Medibuntu repository open a terminal **Applications > accessories >terminal**
and copy and paste the following commands ```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

``` and ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
``` then ```
sudo apt-get update
``` and then ```
sudo apt-get install skype
```

This assumes you are on Ubuntu 7.10 -Gutsy

Good luck

---

### Post by betsy_kevin on 2008-01-21
[B]This gets more and more complex - thanks for your suggestion, but when I do that I get:
[/B]

kevin@kevin-desktop:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libqt4-core (>= 4.3.2) but it is not installable
         Depends: libqt4-gui (>= 4.3.2) but it is not installable
         Depends: dbus-x11 (>= 1.0.0) but it is not installable
E: Broken packages

---

### Post by plucky on 2008-01-21
betsy_kevin,

Can you open a terminal ```
cat /etc/apt/sources.list
``` and copy and paste the output here. The reason you should have unmet dependencies is if not all the repositories are available or you have broken packages in Synaptic.

---

### Post by betsy_kevin on 2008-01-21
Wow:
kevin@kevin-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
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
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
kevin@kevin-desktop:~$

---

### Post by betsy_kevin on 2008-01-21
Geez what does that all mean?

---

### Post by plucky on 2008-01-21
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
# deb http://packages.medibuntu.org/ gutsy free non-free
deb http://packages.medibuntu.org/ gutsy free non-free

```

This shows the non of the **Ubuntu** repositories are enabled.
In the bar the to you need to go into **System > Administration > Software Sources**
and on the first page make sure the first four boxes are filled, and the box in the window for the CD-Rom is un-ticked.Once that is done you need to reload the repositories and then try the Skype installation.

The # in front of the lines beginning with deb means the lines are commented out and so that repository is not enabled. Hope this makes sense.



Good Luck.

---

### Post by betsy_kevin on 2008-01-21
****sigh****

Thanks with your help I feel I'm getting closer, I almost have skype installed but now I get this message:
(did this attach, it's a terminal screenshot saying
there's a conflicting package and it's not installing)

This wouldn't be so important, but we have a lot of international guests who like to call home etc.

---

### Post by betsy_kevin on 2008-01-21
Well thanks everyone, I think I'll pack it in for tonight - if anyone has any ideas about solving this, please share your ideas with me and I'll try it tomorrow and thanks again.
regards, kevin

---

### Post by plucky on 2008-01-22
betsy_kevin,

You already have skype v1.4 installed. Go into **System > Admin > Synaptic** and search for Skype and mark for complete removal and then do ```
sudo apt-get install skype
```
This is what you should get ```
sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dbus-x11 libaudio2 libqt4-core libqt4-gui skype-common
Suggested packages:
  nas
Recommended packages:
  qt4-qtconfig
The following NEW packages will be installed
  dbus-x11 libaudio2 libqt4-core libqt4-gui skype skype-common
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.0MB of archives.
After unpacking 38.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://archive.ubuntu.com gutsy/main dbus-x11 1.1.1-3ubuntu4 [34.8kB]
Get: 2 http://packages.medibuntu.org gutsy/non-free skype-common 2.0.0.27-0medibuntu1 [2074kB]
Get: 3 http://archive.ubuntu.com gutsy/main libaudio2 1.9-2 [77.5kB]
Get: 4 http://archive.ubuntu.com gutsy-updates/main libqt4-core 4.3.2-0ubuntu3.1 [1768kB]
Get: 5 http://archive.ubuntu.com gutsy-updates/main libqt4-gui 4.3.2-0ubuntu3.1 [4887kB]
Get: 6 http://packages.medibuntu.org gutsy/non-free skype 2.0.0.27-0medibuntu1 [13.2MB]
Fetched 22.0MB in 5m45s (63.7kB/s)                                             
Selecting previously deselected package dbus-x11.
(Reading database ... 95462 files and directories currently installed.)
Unpacking dbus-x11 (from .../dbus-x11_1.1.1-3ubuntu4_i386.deb) ...
Selecting previously deselected package libaudio2.
Unpacking libaudio2 (from .../libaudio2_1.9-2_i386.deb) ...
Selecting previously deselected package libqt4-core.
Unpacking libqt4-core (from .../libqt4-core_4.3.2-0ubuntu3.1_i386.deb) ...
Selecting previously deselected package libqt4-gui.
Unpacking libqt4-gui (from .../libqt4-gui_4.3.2-0ubuntu3.1_i386.deb) ...
Selecting previously deselected package skype-common.
Unpacking skype-common (from .../skype-common_2.0.0.27-0medibuntu1_all.deb) ...
Selecting previously deselected package skype.
Unpacking skype (from .../skype_2.0.0.27-0medibuntu1_i386.deb) ...
Setting up dbus-x11 (1.1.1-3ubuntu4) ...
Setting up libaudio2 (1.9-2) ...

Setting up libqt4-core (4.3.2-0ubuntu3.1) ...

Setting up libqt4-gui (4.3.2-0ubuntu3.1) ...

Setting up skype-common (2.0.0.27-0medibuntu1) ...
Setting up skype (2.0.0.27-0medibuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```


Good luck

---

### Post by betsy_kevin on 2008-01-22
Thanks you so much, I finally got it working tonight. We host a lot of international students and it means a lot to them (and to me) that they can talk with their friends and family!

---

### Post by stchman on 2008-01-22
> **betsy_kevin said:**
> Hiya everyone-
My linux project is up and running - thanks everyone - Now I'm trying to install skype, after I download the package and double click to install it, I get a message:


Error: Dependency is not satisfiable: libq4-core


Boy, I dont want that..how do I satisfy my core and load skype (donuts?)

Thanks!!

Skype is available through Medibuntu.  TO install skype through Medibuntu do the following:

I am going to assume you are running Gutsy.
```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get update 

sudo apt-get -y install skype

```

That should do it.

If you are using Feisty, then change gutsy.list to feisty.list in the first line.

---

### Post by Derspankster on 2008-03-17
I get Skype installed but when I try to start it, I get an end user agreement that flashes on the desktop briefly and closes. Skype never starts.

---

### Post by marko@dxlinux on 2008-03-17
i have the same problem. i would install skype on my laptop buti cant install it 'cause from the skype site clicking on download ubuntu version i have problems and i dont know how use the command line from the terminal window . to be more precise i know what i should write in the command line  "sudo apt-get install skype" but i dont know how run that.    if someone has suggestions, thanks.

---

### Post by Derspankster on 2008-03-17
> **marko@dxlinux said:**
> i have the same problem. i would install skype on my laptop buti cant install it 'cause from the skype site clicking on download ubuntu version i have problems and i dont know how use the command line from the terminal window . to be more precise i know what i should write in the command line  "sudo apt-get install skype" but i dont know how run that.    if someone has suggestions, thanks.

Applications>Accessories>Terminal  When the terminal window opens either type in sudo apt-get install skype or just copy and paste it in.  You will be prompted for your password, type it in and hit enter.  The rest will be automatic. You should find the Skype link installed under Applications>Internet.

Actually my problem is different than what you describe.  You need not download the program from the Skype site although you can if you wish. You can also install from Synaptic as well.

---

### Post by Derspankster on 2008-03-18
Here's the solution from another topic posting.

 Originally Posted by plucky  View Post
olgita,

Just a thought,have you tried deleting the .Skype hidden folder in your home directory?

Skype should then try to recreate it and open the license agreement page.

This will fix the problem.

---

