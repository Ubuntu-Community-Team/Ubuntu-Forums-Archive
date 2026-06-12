---
title: "DSL questions"
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by raynor on 2006-05-26
ok i know what version of linux i need but im not done bothering you guys yet:p 

firstly does dsl have to be a live cd

wheres a link to a download that is a non live cd version

my bios does not support cd-rom boot can i still install it with no operating system 

thats all for now but many more to come;)

---

### Post by ubuntu27 on 2006-05-26
> **raynor]ok i know what version of linux i need but im not done bothering you guys yet:p 

firstly does dsl have to be a live cd

wheres a link to a download that is a non live cd version

my bios does not support cd-rom boot can i still install it with no operating system 

thats all for now but many more to come said:**
> 

From the DSL read me file:


[QUOTE]There are currently four types of [Damn Small Linux]("http://www.damnsmalllinux.org/")

dsl-<version>.iso: the standard isolinux version, which is used for liveCD, 
frugal, or traditional harddrive install.

dsl-<version>-syslinux.iso: boots using syslinux instead of isolinux, 
used for some very old hardware that is no longer supported by isolinux.  
Use syslinux version if booting fails with the standard iso.

dsl-<version>-embedded.zip: comes with qemu, for running inside of a host 
Windows or Linux system.

dsl-<version>-vmx.zip:  a virtual machine that will run in VMware or 
VMware player.

frugal_lite.sh is our network install script and requires tomsrtbt linux:
[http://www.toms.net/rb/](http://www.toms.net/rb/)

Docs are located in the pdfdocs/ directory and in the DSL Wiki

So if my guess is that you need to download the "dsl-2.4.iso" file from the [Download page]("http://www.damnsmalllinux.org/download.html")

I have installed DSL in one of my computers using the "Frug install" I believe.
DSL's Hard Drive install is still in Beta, but I haven't seen any problems.
But if you encounter any problems, you better go ask in the DSL Forum: [http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi)


By the way this is Ubuntu Linux Distribution Forum, not DSL :D


EDIT:  You cannot boot from the CD? Then try booting using Floopy Disk following the instructions provided by DSL Wiki:

[http://damnsmalllinux.org/wiki/index.php/Boot_Floppies](http://damnsmalllinux.org/wiki/index.php/Boot_Floppies)

---

