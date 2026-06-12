---
title: "Install:SO-SO-SO close? What does this code mean?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by raker t on 2007-06-03
I've tried all kinds of stuff to install Inkscape on Ubuntu v 5.04. (Fiesty CDs in the mail)
Even though I'll upgrade, I still want to learn how to install this software (without internet)
 I downloaded the two extra files needed (autopackage), extracted them, made them executable (chmod +x) then installed the autopackage(I think).  I tried a couple ways to install the Inkscape, it always says the extra files are still needed. I took all the files from their child files, copied and moved them to the parent file, so as to be sure all the autopackage stuff is actually in the same directory as the Inkscape. Finally, I tried sudo ./install, thought I was a lot closer, but, it appears that it still can't find the autopackage stuff, that is, if I'm reading this code with any semblance of accuracy.

Please help, I've sunk my teeth in this project, I don't want to turn loose just yet. Here's the code:
******************************

jimmo@ubuntumeeoh:~$ cd /var/tmp
jimmo@ubuntumeeoh:/var/tmp$ sudo ./install inkscape-0.45.1.x86.package
Password:
./install: line 38: cd: /var/tmp/share: No such file or directory
./install: line 39: ../etc/config: No such file or directory
autopackage 1.0.7 install tools script, (c) 2002-2005 the autopackage developers
--------------------------------------------------------------------------
  autopackage - the distro neutral packaging framework for Linux systems
--------------------------------------------------------------------------

      Press any key to INSTALL autopackage tools or Ctrl-C to CANCEL.
l
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
Installing Autopackage...
cp: cannot stat `/var/tmp/etc/config': No such file or directory
cp: cannot stat `/var/tmp/share/apkg-bashlib': No such file or directory
cp: cannot stat `/var/tmp/share/apkg-db': No such file or directory
cp: cannot stat `/var/tmp/share/apkg-defs': No such file or directory
cp: cannot stat `/var/tmp/share/apkg-dep': No such file or directory
cp: cannot stat `/var/tmp/share/apkg-failsafelib': No such file or directory
cp: cannot stat `/var/tmp/share/apkg-funclib': No such file or directory
cp: cannot stat `/var/tmp/share/apkg-io': No such file or directory
cp: cannot stat `/var/tmp/share/apkg-script-utils': No such file or directory
cp: cannot stat `/var/tmp/share/apkg-ttyfe': No such file or directory
cp: cannot stat `/var/tmp/share/locale': No such file or directory
cp: cannot stat `/var/tmp/share/remove': No such file or directory
Refreshing linker cache, please wait ... done
apkg-bashlib: line 1119: /etc/autopackage/config: No such file or directory
rm: cannot remove `/etc/autopackage/config': No such file or directory
apkg-bashlib: line 1119: 7: Bad file descriptor
Autopackage setup is finished and completed.
OK to download and install graphical interface now? (Y/n): y


Attempting download of [http://autopackage.org/downloads/1.0.7/autopackage-gtk-1.0.7.x86.package](http://autopackage.org/downloads/1.0.7/autopackage-gtk-1.0.7.x86.package) ...
--19:30:15--  [http://autopackage.org/downloads/1.0.7/autopackage-gtk-1.0.7.x86.package](http://autopackage.org/downloads/1.0.7/autopackage-gtk-1.0.7.x86.package)
           => `autopackage-gtk-1.0.7.x86.package'
Resolving autopackage.org... failed: Host not found.
Download failed.


Attempting download of [http://www.wildgardenseed.com/autopackage/1.0.7/autopackage-gtk-1.0.7.x86.package](http://www.wildgardenseed.com/autopackage/1.0.7/autopackage-gtk-1.0.7.x86.package) ...
--19:30:15--  [http://www.wildgardenseed.com/autopackage/1.0.7/autopackage-gtk-1.0.7.x86.package](http://www.wildgardenseed.com/autopackage/1.0.7/autopackage-gtk-1.0.7.x86.package)
           => `autopackage-gtk-1.0.7.x86.package'
Resolving [www.wildgardenseed.com](www.wildgardenseed.com)... failed: Host not found.
Download failed.


Attempting download of [http://www.allaboutgames.co.uk/autopackage/1.0.7/autopackage-gtk-1.0.7.x86.package](http://www.allaboutgames.co.uk/autopackage/1.0.7/autopackage-gtk-1.0.7.x86.package) ...
--19:30:15--  [http://www.allaboutgames.co.uk/autopackage/1.0.7/autopackage-gtk-1.0.7.x86.package](http://www.allaboutgames.co.uk/autopackage/1.0.7/autopackage-gtk-1.0.7.x86.package)
           => `autopackage-gtk-1.0.7.x86.package'
Resolving [www.allaboutgames.co.uk](www.allaboutgames.co.uk)... failed: Host not found.
Download failed.


jimmo@ubuntumeeoh:/var/tmp$

********************************
THANKS!:)

---

### Post by N8K99 on 2007-06-03
you may need some additional packages ( not 100%  on this) such as build-essential and gcc. i would like to suggest just using the apt-get install method for inkscape as that is one of the finer points to a debian based distro such as ubuntu, simplified package installation.

---

### Post by Lucifiel on 2007-06-03
Hmmm... given that said poster does not have internet(I'm assuming that is the case), hmmm... perhaps he can try and get a deb package for Inkscape and put it on a thumbdrive or something. 

Note: there are 2 types of deb packages. 1 for Debian and 1 for Ubuntu. So, make sure you get the right one or the deb might not install.

---

### Post by raker t on 2007-06-03
Thank_you_for_the_help!:)

I'll try the apt get install.
 My arrangement is that I put a second HD in this box, that's where Ubuntu is, the other HD has MSwindows and the internet. I move files back and forth with a flash drive.

 Three questions, second one might be trivial: 

1. So you DON'T think this is a problem involving "misplaced" autopackage content?
 2.Everybody keeps talking about a file named "autopackage.tar.bz2" What I actually got was "autopackage.tar.tar" Does that make any difference? I'm pretty sure it did extract, although it created a child folder in the process, don't know if that matters.
3. Somewhere, I recall seeing something like the need to have the autopackage installed BEFORE you try the package install, like the package has this reaction/memory deal. If this is so, I would need to delete/reload the package.

I'll go look for a Debian version.

---

### Post by Lucifiel on 2007-06-03
Hmmm... internet doesn't work on Ubuntu, huh? :p

That's a pain, man. Actually, you can access your Windows partition with the ntfs-3g tool but you'd likely need internet to install it.

1. "misplaced" autopackage content? Pardon?

2. Hmmm... I think there's not too much of a difference. What you need to do is watch out for the contents of the unzipped folder.

3. Sorry I don't know anything about autopackages. I did find out that they're supposed to be package system which works across multiple distributions of Linux?

---

### Post by raker t on 2007-06-03
lol, I know "misplaced" sounds dumb, but....

I've got these files "all OVER the place". Actually, just in the parent and child folders. When extracted, the autopackage made a few subfolders (child?) with 'stuff' in them. 

The attempted installs keep acting like the autopackage files are not available, so I copied the 'stuff' from the sub folders right into the directory where the Inkscape package is. Now it's both places, and I made it uxecutable, both places, and installed it both places.

It IS a pain not having internet with the ubuntu. From what I understand, this whole install would have probably been done a week ago if it were. The problem is that ubuntu gets a bit difficult with -get this- dial up (there I said it) modems. I'm seriously looking at DSL, but every financial decision I make must be weighed carefully. I'll sapre you the pages detailing the political and spiritual reasoning and activism. For the moment, no internet with ubuntu. Besides, I'd like to duplicate this whole process on my laptop. Saturday night, here you are reading this stuff, strange yes, but at least it's not fiction.

Yes, autopackage is a multiple distro install. I just got back fron the Inkscape site, there is a debian version. I would have to download, maybe biuld, compile/configure (whatever that word was) then install.... Interesting.

Thanks again for the help, seriously. I did notice a head against the wall emoticon, I'm thinking I need one where the guy's in a golf cart with itty-bitty wheels, he hits a pea sized bit of gravel, and it feels like a mountain. I just know this is some liitle glitch I'm not doing right. Like the time I spent a couple months getting a pen plotter I bought without a manual to work. I could do that intall in 4 minutes now.

---

### Post by hyper_ch on 2007-06-03
Why don't you download the .deb packages directly from the ubuntu packages:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

the .deb files are precompiled and much easier to install... those are the packages that synaptic and adept and apt-get and aptitude fetch if you do an "internet-based" install..

---

### Post by Lucifiel on 2007-06-03
> **hyper_ch said:**
> Why don't you download the .deb packages directly from the ubuntu packages:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

the .deb files are precompiled and much easier to install... those are the packages that synaptic and adept and apt-get and aptitude fetch if you do an "internet-based" install..

If you'd searched within that site, you'd have found out that Inkscape doesn't have a deb file for Dapper. :p

---

### Post by hyper_ch on 2007-06-03
Oh.... I didn't read right and he said (Feisty) in brackets and so I just thought he made a typo of 5.04 instead of 7.04 ^^ my mistake

---

### Post by Lucifiel on 2007-06-03
Hmmm...
Okay, I've found out how to get .package to run.

First, this is the .package for Inkscape: [http://downloads.sourceforge.net/inkscape/inkscape-0.45.1.x86.package](http://downloads.sourceforge.net/inkscape/inkscape-0.45.1.x86.package)

This is how to get the .package to run:
[http://autopackage.org/docs/howto-install/?PHPSESSID=88c9654dc1e95a8778dd6ccb9ad60f30](http://autopackage.org/docs/howto-install/?PHPSESSID=88c9654dc1e95a8778dd6ccb9ad60f30)

---

