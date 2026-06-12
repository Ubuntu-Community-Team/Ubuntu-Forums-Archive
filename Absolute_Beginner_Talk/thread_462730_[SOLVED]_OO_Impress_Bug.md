---
title: "[SOLVED] OO Impress Bug ?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-03
Whenever I use Impress to view a PowerPoint (its sent to me by windows users  :P ), after i finish the slideshow, i always get this window on closing Impress. (see screenshot please )

Once i click OK on this error message OO Writer opens up.

Is this a bug or just my installation? BTW, i did not install OO, i am using the one that came with Ubuntu

---

### Post by FuturePilot on 2007-06-03
It's a well known bug. It's been reported on Launchpad. Who knows when it will be fixed though. It's been around since Feisty Herd 5. Someone said that the latest Debian OO packages worked fine.
Feel free to add a comment
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/90513]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/90513")

I like your wallpaper by the way.

---

### Post by Inxsible on 2007-06-03
I read on the link that if we remove the Ubuntu pre-installed version of OO, and install it from [Open Office]("http://www.openoffice.org") then the bug goes away.

1) So my question would be, if I remove the pre-installed version, will i have to remove ubuntu-desktop as well?
Coz to remove the pre-installed software like sound juicer or evolution, we also have to remove ubuntu-desktop. I was wondering if it was the same with pre-installed OO

2) If I do remove pre-installed OO, should I remove all packages like libhunspell-1.1-0, openoffice-core, openoffice-common, openoffice.org-gnome, openoffice.org-gtk and a bunch of others? Will these be re-installed when i install the version from OO.

I am concerned about the openoffice.org-gnome and the openoffice.org-gtk, since OO doesnt have any deb packages, they have only rpm so I was wondering if all the bindings will be properly installed in Debian based distros like Ubuntu.

OR if I dont remove the gnome related packages, will the bug stay ?

Thanks guys !

---

### Post by vanadium on 2007-06-03
It is indeed an ugly bug: you are in front of an audience with. 

1) You will need to remove the Ubuntu Desktop metapackage, but that does not mean that any of the other "real" packages will/must be removed. I am not sure however about side effects of removing Ubuntu Desktop package, for example, for automatic updating.

2) You can remove them all. All needed packages come with the official installer.

There is 'gnome integration' with the official installer, but the icons are different: the original OOo icons remain.

---

### Post by Inxsible on 2007-06-03
> **vanadium said:**
> It is indeed an ugly bug: you are in front of an audience with. 

1) You will need to remove the Ubuntu Desktop metapackage, but that does not mean that any of the other "real" packages will/must be removed. I am not sure however about side effects of removing Ubuntu Desktop package, for example, for automatic updating.

2) You can remove them all. All needed packages come with the official installer.

There is 'gnome integration' with the official installer, but the icons are different: the original OOo icons remain.

Removing ubuntu-desktop can cause nightmares during updates...which I am planning to stay away from :)

I really dont give a damn about icons...I will probably like the new ones as well

---

### Post by Inxsible on 2007-06-03
I know I will have to install the official installer thru Alien, as they only provide a RPM and not a DEB.

I have never used alien, so will i have to keep alien around after installing and run it via alien (something similar to what wine does-- you need to run those programs thru wine )

Or is Alien only used to install and you can get rid of it once you are done ?

---

### Post by FuturePilot on 2007-06-03
All you need Alien for is for converting the RPMs to .debs. If you want you can get rid of it afterwards.
Here's a good How To
[http://ubuntuforums.org/showthread.php?t=398074]("http://ubuntuforums.org/showthread.php?t=398074")

---

### Post by Inxsible on 2007-06-03
Thanks FuturePilot

---

### Post by Inxsible on 2007-06-03
The problem is that I will have to un-install ubuntu-desktop.

I am not too fluent with Linux to be confident of doing that !  :(

---

### Post by FuturePilot on 2007-06-03
Removing the Ubuntu-desktop package shouldn't cause you any problems. It would only cause problems when doing a distro upgrade like from Feisty to Gutsy.

---

### Post by stchman on 2007-06-11
> **Inxsible said:**
> I read on the link that if we remove the Ubuntu pre-installed version of OO, and install it from [Open Office]("http://www.openoffice.org") then the bug goes away.

1) So my question would be, if I remove the pre-installed version, will i have to remove ubuntu-desktop as well?
Coz to remove the pre-installed software like sound juicer or evolution, we also have to remove ubuntu-desktop. I was wondering if it was the same with pre-installed OO

2) If I do remove pre-installed OO, should I remove all packages like libhunspell-1.1-0, openoffice-core, openoffice-common, openoffice.org-gnome, openoffice.org-gtk and a bunch of others? Will these be re-installed when i install the version from OO.

I am concerned about the openoffice.org-gnome and the openoffice.org-gtk, since OO doesnt have any deb packages, they have only rpm so I was wondering if all the bindings will be properly installed in Debian based distros like Ubuntu.

OR if I dont remove the gnome related packages, will the bug stay ?

Thanks guys !

I have a script that removes your Openoffice.org from Feisty and installs Openoffice.org 2.2 gotten from OO's website.

Yes, the Impress bug does not exist in this version.  Be warned the fonts on the OO2.2 gotten from OO's website look rotten IMO.  Ubuntu as excellent fonts on their 2.2 version.  If you want then get my script here:

[http://www.stchman.com/tools/OO_install.sh](http://www.stchman.com/tools/OO_install.sh)

The script will delete your old OO and install OO2.2 from a package that I did the alien conversion.  I have tested this script and it works well.

Don't crab about the fonts looking bad.

---

