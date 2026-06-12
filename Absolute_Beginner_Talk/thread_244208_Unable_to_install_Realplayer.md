---
title: "Unable to install Realplayer"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2006-08-26
Hi,
I remember on my last Ubuntu installation I easily added Realplayer 10.0 using Add/Remove.  When the recent X-server update problem happend I reinstalled Ubuntu 6.06.1 once again (before realizing a solution was posted on the website).  Now I'm trying to add Realplayer and I get this warning 

"Cannot install 'realplayer'
This application conflicts with other installed software. To install 'realplayer' the conflicting software must be removed before.
Switch to the advanced mode to resolve this conflict."

when I try to use synaptic I get another box saying

"Could not mark all packages for installation or upgrade.
The following packages have unresolved dependencies.  Make sure that all required repositories are added and enabled in the preferencess.
realplayer: depends: xlibs but not installable."

BTW I did add the Universe and Multiverse repositories

---

### Post by Perfect Storm on 2006-08-26
Do you have any unofficial repo in your sourcelist which might make a conflict?

---

### Post by SteelCore on 2006-08-26
I'm afraid I don't really know. I included all the warning messages I got in my original post.  That is all I know about this problem.

---

### Post by kaamos on 2006-08-26
Just tested, I get this as well with xgl packages from quinn installed. Aptitude says that xlibs is a metapackage so the dependencies are not filled.

**SteelCore**: please post the contents of the file /etc/apt/sources.list

---

### Post by Perfect Storm on 2006-08-26
okay.

Lets first try with:
```
sudo aptitude install realplay
```
Does it solve it? If not what error output does it show?

Edit: Okay I see someone know the specific problem.

---

### Post by SteelCore on 2006-08-26
This is the /etc/apt/sources.list contents:

"deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe"

---

### Post by SteelCore on 2006-08-26
> **Artificial Intelligence said:**
> okay.

Lets first try with:
```
sudo aptitude install realplay
```
Does it solve it? If not what error output does it show?

Edit: Okay I see someone know the specific problem.

Here's what I got

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find package "realplay". However, the following
packages contain "realplay" in their name:
  realplayer
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by Perfect Storm on 2006-08-26
Backup your sourcelist.
Then change your sourcelist with this one:
> # Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# Penguin Liberation Front (sources)
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free

# Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## dapper-commercial by canonical
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


by doing this:
```
sudo nano /etc/apt/sources.list
```

Then updating it into:
```
sudo apt-get update
```

try again then.

---

### Post by Crosbie on 2006-08-26
> **SteelCore said:**
> Here's what I got

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find package "realplay". However, the following
packages contain "realplay" in their name:
  realplayer
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

Hang on - isn't there a problem right there?  The package is called 'realplayer' rather than just 'realplay'?

---

### Post by Perfect Storm on 2006-08-26
realplayer is v. 8.x
realplay is v. 10.x

---

### Post by SteelCore on 2006-08-26
> **Artificial Intelligence said:**
> Backup your sourcelist.
Then change your sourcelist with this one:


by doing this:
```
sudo nano /etc/apt/sources.list
```

Then updating it into:
```
sudo apt-get update
```

try again then.

Sorry but once I enter the first (sudo nano /etc/apt/sources.list) I don't know how to get the command prompt -$ again

---

### Post by Perfect Storm on 2006-08-26
ah, sorry.

<ctrl>+<o> = Save
<ctrl>+<x> = Exit

---

### Post by Crosbie on 2006-08-26
> **Artificial Intelligence said:**
> realplayer is v. 8.x
realplay is v. 10.x

Ah thanks, I didn't know that.  *stops poking nose in* :)

---

### Post by Perfect Storm on 2006-08-26
> **Crosbie said:**
> Ah thanks, I didn't know that.  *stops poking nose in* :)

It's a fair question :)

---

### Post by SteelCore on 2006-08-26
> **Artificial Intelligence said:**
> ah, sorry.

<ctrl>+<o> = Save
<ctrl>+<x> = Exit

OK I did that.  I then opened synaptic to install realplayer again but still got:
"Could not mark all packages for installation or upgrade.
The following packages have unresolved dependencies. Make sure that all required repositories are added and enabled in the preferencess.
realplayer: depends: xlibs but not installable."

---

### Post by SteelCore on 2006-08-26
I think that my sources.list has not been changed

---

### Post by Perfect Storm on 2006-08-26
Strange...
try the
```
sudo aptitude install realplay
```
again (remember to close synaptic first).

Hmmmm....any chance you had Compiz and XGL repo. in your sourcelist once?

---

### Post by Perfect Storm on 2006-08-26
> **SteelCore said:**
> I think that my sources.list has not been changed

You did the 
```
sudo apt-get update
```
right?

---

### Post by SteelCore on 2006-08-26
> **Artificial Intelligence said:**
> Strange...
try the
```
sudo aptitude install realplay
```
again (remember to close synaptic first).

Hmmmm....any chance you had Compiz and XGL repo. in your sourcelist once?

You mean
sudo aptitude install realplayer

I did that but I still get the error about resolving the dependencies.
I'm not positive that my souces.list has not been changed. I probably could not follow your guidance properly...

---

### Post by SteelCore on 2006-08-26
> **Artificial Intelligence said:**
> Strange...
try the
```
sudo aptitude install realplay
```
again (remember to close synaptic first).

Hmmmm....any chance you had Compiz and XGL repo. in your sourcelist once?

this is actually a fresh ubuntu install from this morning. Besides the install and the update plus adding universe and multiverse I did nothing

---

### Post by Perfect Storm on 2006-08-26
okay let's try again :)

First, lets check if you have the sourcelist correctly setup:
```
cat /etc/apt/sources.list
```
please post the output.

---

### Post by kaamos on 2006-08-26
I'm beginning to get the feeling that the realplayer package is broken in the repos.

```
**$ apt-cache show realplayer**
Package: realplayer
Priority: optional
Section: multiverse/net
Installed-Size: 208
Maintainer: Christian Marillat <marillat@debian.org>
Architecture: i386
Version: 8.0.11
Replaces: rvplayer
Provides: rvplayer
Depends: debconf (>= 0.9.53), xlibs, libc6, cpio
Suggests: netscape
Conflicts: rvplayer
Filename: pool/multiverse/r/realplayer/realplayer_8.0.11_i386.deb
Size: 22534
MD5sum: 383b165af4de00b0c0d1936bea38a992
Description: Real Player (installer)
 Real Player is a streaming sound and video player from RealNetworks.
 .
 RealNetworks does not allow redistribution of their software. Therefore,
 this package requires the user to fetch the real player archive separately
 from their web site. When you install this package you will be guided
 through that process.
 .
 This package installs the file rp8_linux20_libc6_i386_cs2_rpm from the
 real.com website (look for the Unix player).
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

```
**$ apt-cache search xlibs**
xcursor-themes - Base X cursor themes
xkeyboard-config - XKB data
xlibs-dev - X Window System client library development files transitional package
xterm - X terminal emulator
libxsharp-dev - DotGNU X11# libraries
libxsharp0 - DotGNU X11# libraries
ude - The Unix Desktop Environment
uwm - The ultimate window manager for UDE

```

---

### Post by Perfect Storm on 2006-08-26
Why are you going after realplayer and not realplay?

---

### Post by kaamos on 2006-08-26
I personally use mplayer instead. ;) Just interested that is there a package with wrong dependencies in multiverse..

---

### Post by SteelCore on 2006-08-26
> **Artificial Intelligence said:**
> okay let's try again :)

First, lets check if you have the sourcelist correctly setup:
```
cat /etc/apt/sources.list
```
please post the output.

Hope this isn't too late but the following is the output
"
deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://jo.archive.ubuntu.com/ubuntu/](http://jo.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
"

---

### Post by Perfect Storm on 2006-08-27
next and remember that linux is case sensitive:

```
sudo nano /etc/apt/sources.list
```

erease the list and fill in this instead:

```
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
deb http://seveas.theplayboymansion.net/seveas dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
deb-src http://mirror.ubuntulinux.nl dapper-seveas all

# Penguin Liberation Front (packages)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Penguin Liberation Front (sources)
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# Bleeding edge wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

## dapper-commercial by canonical
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

Save and exit ( <ctrl> + <o> | <ctrl> + <x> )

Now check if the sourcelist is the same as I have given you:

```
cat /etc/apt/sources.list
```

If it is continue, if not try again.

Next:
```
sudo apt-get update
```
Now it may complain about something about "keys". The key is the number you'll see listed above every source.
eg:
> # Seveas' packages (sources, GPG key: **1135D466**)
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all
Put every key complain into this command, where XXXXXXXX = key complain:
```
gpg --keyserver subkeys.pgp.net --recv XXXXXXXX
gpg --export --armor XXXXXXXX | sudo apt-key add -
```

When done,  run this command again:
```
sudo aptitude update
```
if it doesn't complain continue.
Now getting realplayer (the one you want to have is called realplay not realplayer) installed:
```
sudo aptitude install realplay
```

---------
A little explaination:
sudo: means "superuser do". This is require when you want to change or modify something outside normal user priveledge.

cat: Shows what eg. a file are containing and display it.

nano: an powerful editor application.

aptitude: is a package application which solve dependency, downloading,upgrading etc. packages.

sources.list: is the list where aptitude and synaptic package manager where they can recieve packages from. When sources.list is setup perfectly you don't need to download applications and libs individually (well in rare cases maybe).

---

### Post by SteelCore on 2006-08-28
Thank you for you help but unfortunately things got stuck when I reached the 'keys' part of your last post.  I opted for the easier solution and reinstalled ubuntu one more time (I've lost count of the total). Using only the default repositories I found RealPlayer 10.0 using Add/Remove.  Strangely it was in the Graphics section but after installation it correctly went to 'Applications>Sound & video'.  Thank you again for your time.

---

### Post by ryan76 on 2006-09-03
Hi, just wanted to say, I followed the instructions above and it worked perfectly! Awesomeness! I had to remove helix-player at the very end then realplay installed fine through synaptic.

Thanks!!!

---

