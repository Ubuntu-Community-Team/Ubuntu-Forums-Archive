---
title: "Slackware  -  I don't get the point?"
date: 2011-05-04
forum: Any Other OS
---

### Post by Fraoch on 2011-05-04
My little project to learn more about Linux has led me to install as many distros as I can think of in VirtualBox, starting with a command-line only install then adding Xorg, Openbox, fbpanel, etc to get a minimal desktop environment consuming a minimum of memory (I also want to discover what distro is the most "efficient").

Incidentally, I started discovering that once you get to the CLI, most Linux distros are the same.  The only difference seems to be how packages are fetched, unpackaged and installed.

I've learned a LOT and I've developed some favourites - Gentoo for sheer efficiency and minimalism at the cost of very long compile times, Arch for its cutting-edge packages and efficiency, and Debian for stability.

One distro I just didn't take to is Slackware.  I've long heard that this is the distro to use if you want to learn Linux.  I didn't find that at all - you're just given everything on a giant 4.2 GB DVD .ISO and it's all installed onto your partitions.  I don't like that Slack doesn't have a consistent method of installing programs - a select few have SlackBuilds, some you install from source code.  There's no concept of an official online repository, it's spread among official sources and third party sources.  I also find the documentation on Slack confusing - there's nothing official, it's spread out all over the place in an inconsistent fashion.

Did I miss something?  Do I just not get it?  Is there a better way to go about getting and learning Slackware?

---

### Post by Tribulation on 2011-05-04
People typically say that Slackware is a great way to learn Linux because it requires you to actually use the command line and edit configuration files manually and such. Slackware these days is a bit more user friendly though, as long as you install everything from the dvd that is. The less you install, the less user friendly it gets. 

As for installation methods, it really is consistence. You install from .tgz (or the other compatible archives) files. However there are quite a bit of third party applications for installing them. There is a repo but it's rather small, slackpkg pulls from it. If you want packages that aren't those repos of course you'll have to get them elsewhere. SlackBuilds is not an officially endorsed Slackware site, though many people use it. By the way, if you haven't already, give sbopkg a shot if you wish. It provides an ncurses interface with which to browse and install SlackBuilds. 

For documentation, take a look at the Slack book, it's got a lot of great information. A new version is currently in the works.

Really, to learn about Slackware the best advice I can give is to use it, visit the forums at Linux Questions, and read the Slackbook.

---

### Post by boydrice on 2011-05-04
> **Fraoch said:**
> 
One distro I just didn't take to is Slackware.  I've long heard that this is the distro to use if you want to learn Linux.  I didn't find that at all - you're just given everything on a giant 4.2 GB DVD .ISO and it's all installed onto your partitions.  I don't like that Slack doesn't have a consistent method of installing programs - a select few have SlackBuilds, some you install from source code.  There's no concept of an official online repository, it's spread among official sources and third party sources.  I also find the documentation on Slack confusing - there's nothing official, it's spread out all over the place in an inconsistent fashion.

Did I miss something?  Do I just not get it?  Is there a better way to go about getting and learning Slackware?

Slackware has a very consistent method to install packages from the official repos using either pkgtool or slackpkg.  These are the official tools, installpkg, removepkg, explodepkg, makepkg, and then slackpkg which is a wrapper around those tools much like apt-get is around dpkg.  Of course none of these tools resolves dependencies as that is what the administrator is for.  

For third-party packages Slackbuilds.org is by far and away the most popular choice.  Think of Slackbuilds.org as an equivalent of the Arch linux's AUR or the Ports system for FreeBSD.  The official method to install a Slackbuild is to do so manual per the instructions on the site there is however a great tool called sbopkg which provides similar features to what slackpkg does only specifically for the slackbuilds repos.  Sbopkg is a fantastic tool that takes some of the intimidation out of the manual slackbuild process and was developed by Chess Griffin (of Linux Reality Podcast fame).  For pre-compiled packages the two most popular spots are Alien Bob's repo and Robby Workman's repo.  Alien Bob (Eric Hameleers) and Robby Workman are part of the Slackware development team and are extremely respected members of the Slackware community.  There are other random package sites for Slackware but none of them are highly thought of as those mentioned above.  I think the confusion for most new users of Slackware is how to keep track of third-party packages.  With Slackbuilds the sbopkg tool makes it very simple to check the changelogs, check for updates online and install them, but for other repos such as Alien Bob or Robby Workman's the choice of how to track or update the packages used from their repos is left up to the user.  It is this choice that really forces the user to learn linux's tools such as rsync, wget, cron, bash scripting, etc.  For example you might choose to mirror the repo and use a cron job to look for updates to their changelogs, then use the default Slackware tools to update accordingly.  It is at this point you are not using a particular distros package manager to do the work for you you need to learn how to do it yourself to make it as easy as you wish.  You are not relying on APT or Yum to start needed (or uneeded) services upon an installation of a package you need to understand what services need to be started and set them to do so.

As for documentation the official set is included right in your DVD medium and housed on the official repos.  There are a set of README and How-To text files that provide you the official documentation set.  There is documentation on installation, changes and hints, LVM setup, encryption setup, RAID setup, creating an initrd to use the generic kernel, and others.  This is the consolidated documentation set you were looking for.  In addition to that there is a print and online book called Slackware Linux Essentials which provides more in-depth information although is in need of an update.  Also there is the community maintained Slackwiki and then of course the comprehensive linux links on the LQ forums which has links to everything noted above and more.

As for the software provided at installation, yes there is quite a selection of software.  The Slackware way is to give you a working functional workstation or server right out of the box.  Slackware does not assume what you want it merely gives you the official package set and lets you decide what you want from it.  You can easily modify what packages you do or do not want at installation time.   One example is if you do not want the KDE desktop just unselect it from the installation menu.  Slackware assumes you know what you are doing and will gladly let you uninstall any package whether or not you might want or need it later this is why the regulars on the LQ forums recommend that new users to Slackware do the full install as this provides all necessary packages, tools and dependancies.

Anyway as you see I could go on and on as I am a huge Slackware fan.  I started out with Linux a couple years ago using Ubuntu, Debian, Fedora, openSUSE, and was unsatisfied.  I was listening to the Linux Reality Podcasts by Chess Griffin and he did two shows almost exclusively on Slackware and I was extremely intrigued by it and you could really sense the passion he had for it.  I finally got an intel machine and tried 12.1 or 12.2, got it installed but the learning curve was too steep for me at that time.  I remember not knowing how to edit a config file using the command line and just not getting it at all.  Did some distro-hopping and kept coming back every so often to Slackware, each time I would learn a little more about linux.  By the time 13.1 rolled around I was hooked and had became a DVD subscriber.  I hope you give it another shot and below are links to all of the stuff mentioned above.

Slackware official readmes and how-to's:
[http://slackware.osuosl.org/slackware-13.37/]("http://slackware.osuosl.org/slackware-13.37/")

Slackbuilds.org:
[http://slackbuilds.org/]("http://slackbuilds.org/")

sbopkg:
[http://www.sbopkg.org/]("http://www.sbopkg.org/")

Slackware Linux Essentials:
[http://www.slackbook.org/html/index.html]("http://www.slackbook.org/html/index.html")

Slackbook
[http://www.slackbook.org/]("http://www.slackbook.org/")

Alien Bob's wiki:
[http://alien.slackbook.org/dokuwiki/doku.php]("http://alien.slackbook.org/dokuwiki/doku.php")

Robby Workman's packages:
[http://rlworkman.net/pkgs/]("http://rlworkman.net/pkgs/")

LQ Forums Slackware Linux Links:
[http://wiki.linuxquestions.org/wiki/Slackware-Links]("http://wiki.linuxquestions.org/wiki/Slackware-Links")

gnomeslackbuilds.org:
[http://gnomeslackbuild.org/]("http://gnomeslackbuild.org/")

---

### Post by krapp on 2011-05-04
> **boydrice said:**
> Of course none of these tools resolves dependencies as that is what the administrator is for.

:shock:

---

### Post by tgalati4 on 2011-05-04
I have often found slackware to have an excellent build environment.  Many times, trying to compile the latest version of a package--audacity, for example, would fail on Ubuntu because some supporting package was out of date.  This is known as a "dependency hell".  You can't install the supporting package because it depends on something else, etc.

The way slackware packages are bundled and the clean build environment (no excessive hacking of major frameworks) means that new packages and home-grown packages tend to build and run successfully.  So I keep a slack box around just for building stuff that fails to build on Ubuntu or Fedora.

Also because slackware was conceived, developed, and assembled by one person (Patrick V.) it has a singular purpose.  It's not an OS by committee with lots of random stuff thrown in and not all of it working.  When you've used slackware for a while, you can sense this singular purpose and I certainly appreciate the effort that went into it.

---

### Post by boydrice on 2011-05-05
> **krapp said:**
> :shock:

Since the default Slackware install includes most needed libraries this isn't as daunting as it sounds.  For example to install the slackbuild for gtkpod here are the deps:

"gtkpod is a platform independent Graphical User Interface for Apple's 
iPod using GTK2. It supports the first to fifth Generation including 
the iPod mini, iPod Photo, iPod Shuffle, iPod nano, and iPod Video.

This requires libgnomecanvas and optionally libmp4v2."

Really it isn't so bad.  There is a big difference between the deps you will see in a .deb or rpm system compared to real runtime dependencies.

---

### Post by 3Miro on 2011-05-05
I was impressed by how smooth Slackware KDE implementation was. I also liked the fact that they have XFCE and not Gnome. I am not hating on Gnome, it is just that way too often Gnome-centric distros will make a "xfce spin" by simply replacing Metacity with Xfwm4 and Nautilus with Thunar. The XFCE spin becomes a tweaked version of Gnome. Not on Slackware.

On the other hand, I felt like Slackware was too restrictive (package wise). There is a small set of software that you can use by default, but if you want something slightly different, things get very tedious. Resolving dependencies and installing additional stuff from SlackBuilds is just no fun. Note that I use Gentoo, so I am definitely not complaining about compiling, it is the manual work of download the file, download the source, type commands to compile, type command to install. On Gentoo this is just one command.

I guess I will have to check sbopkg, this may be the thing that I am missing.

---

### Post by joshuapurcell on 2011-05-06
> **boydrice said:**
> Slackware has a very consistent method to install packages from the official repos using either pkgtool or slackpkg.  These are the official tools, installpkg, removepkg, explodepkg, makepkg, and then slackpkg which is a wrapper around those tools much like apt-get is around dpkg.  Of course none of these tools resolves dependencies as that is what the administrator is for.  

For third-party packages Slackbuilds.org is by far and away the most popular choice.  Think of Slackbuilds.org as an equivalent of the Arch linux's AUR or the Ports system for FreeBSD.  The official method to install a Slackbuild is to do so manual per the instructions on the site there is however a great tool called sbopkg which provides similar features to what slackpkg does only specifically for the slackbuilds repos.  Sbopkg is a fantastic tool that takes some of the intimidation out of the manual slackbuild process and was developed by Chess Griffin (of Linux Reality Podcast fame).  For pre-compiled packages the two most popular spots are Alien Bob's repo and Robby Workman's repo.  Alien Bob (Eric Hameleers) and Robby Workman are part of the Slackware development team and are extremely respected members of the Slackware community.  There are other random package sites for Slackware but none of them are highly thought of as those mentioned above.  I think the confusion for most new users of Slackware is how to keep track of third-party packages.  With Slackbuilds the sbopkg tool makes it very simple to check the changelogs, check for updates online and install them, but for other repos such as Alien Bob or Robby Workman's the choice of how to track or update the packages used from their repos is left up to the user.  It is this choice that really forces the user to learn linux's tools such as rsync, wget, cron, bash scripting, etc.  For example you might choose to mirror the repo and use a cron job to look for updates to their changelogs, then use the default Slackware tools to update accordingly.  It is at this point you are not using a particular distros package manager to do the work for you you need to learn how to do it yourself to make it as easy as you wish.  You are not relying on APT or Yum to start needed (or uneeded) services upon an installation of a package you need to understand what services need to be started and set them to do so.

As for documentation the official set is included right in your DVD medium and housed on the official repos.  There are a set of README and How-To text files that provide you the official documentation set.  There is documentation on installation, changes and hints, LVM setup, encryption setup, RAID setup, creating an initrd to use the generic kernel, and others.  This is the consolidated documentation set you were looking for.  In addition to that there is a print and online book called Slackware Linux Essentials which provides more in-depth information although is in need of an update.  Also there is the community maintained Slackwiki and then of course the comprehensive linux links on the LQ forums which has links to everything noted above and more.

As for the software provided at installation, yes there is quite a selection of software.  The Slackware way is to give you a working functional workstation or server right out of the box.  Slackware does not assume what you want it merely gives you the official package set and lets you decide what you want from it.  You can easily modify what packages you do or do not want at installation time.   One example is if you do not want the KDE desktop just unselect it from the installation menu.  Slackware assumes you know what you are doing and will gladly let you uninstall any package whether or not you might want or need it later this is why the regulars on the LQ forums recommend that new users to Slackware do the full install as this provides all necessary packages, tools and dependancies.

Anyway as you see I could go on and on as I am a huge Slackware fan.  I started out with Linux a couple years ago using Ubuntu, Debian, Fedora, openSUSE, and was unsatisfied.  I was listening to the Linux Reality Podcasts by Chess Griffin and he did two shows almost exclusively on Slackware and I was extremely intrigued by it and you could really sense the passion he had for it.  I finally got an intel machine and tried 12.1 or 12.2, got it installed but the learning curve was too steep for me at that time.  I remember not knowing how to edit a config file using the command line and just not getting it at all.  Did some distro-hopping and kept coming back every so often to Slackware, each time I would learn a little more about linux.  By the time 13.1 rolled around I was hooked and had became a DVD subscriber.  I hope you give it another shot and below are links to all of the stuff mentioned above.

Slackware official readmes and how-to's:
[http://slackware.osuosl.org/slackware-13.37/]("http://slackware.osuosl.org/slackware-13.37/")

Slackbuilds.org:
[http://slackbuilds.org/]("http://slackbuilds.org/")

sbopkg:
[http://www.sbopkg.org/]("http://www.sbopkg.org/")

Slackware Linux Essentials:
[http://www.slackbook.org/html/index.htm]("http://www.slackbook.org/html/index.htm")l

Alien Bob's wiki:
[http://alien.slackbook.org/dokuwiki/doku.php]("http://alien.slackbook.org/dokuwiki/doku.php")

Robby Workman's packages:
[http://rlworkman.net/pkgs/]("http://rlworkman.net/pkgs/")

LQ Forums Slackware Linux Links:
[http://wiki.linuxquestions.org/wiki/Slackware-Links]("http://wiki.linuxquestions.org/wiki/Slackware-Links")

gnomeslackbuilds.org:
[http://gnomeslackbuild.org/]("http://gnomeslackbuild.org/")
Awesome thanks for all the info on Slackware, you have talked me into checking this distro out more closely.

---

### Post by Fraoch on 2011-05-06
> **boydrice said:**
> Slackware has a very consistent method to install packages from the official repos using either pkgtool or slackpkg.  These are the official tools, installpkg, removepkg, explodepkg, makepkg, and then slackpkg which is a wrapper around those tools much like apt-get is around dpkg.  Of course none of these tools resolves dependencies as that is what the administrator is for.  

For third-party packages Slackbuilds.org is by far and away the most popular choice.  Think of Slackbuilds.org as an equivalent of the Arch linux's AUR or the Ports system for FreeBSD.  The official method to install a Slackbuild is to do so manual per the instructions on the site there is however a great tool called sbopkg which provides similar features to what slackpkg does only specifically for the slackbuilds repos.  Sbopkg is a fantastic tool that takes some of the intimidation out of the manual slackbuild process and was developed by Chess Griffin (of Linux Reality Podcast fame).  For pre-compiled packages the two most popular spots are Alien Bob's repo and Robby Workman's repo.  Alien Bob (Eric Hameleers) and Robby Workman are part of the Slackware development team and are extremely respected members of the Slackware community.  There are other random package sites for Slackware but none of them are highly thought of as those mentioned above.  I think the confusion for most new users of Slackware is how to keep track of third-party packages.  With Slackbuilds the sbopkg tool makes it very simple to check the changelogs, check for updates online and install them, but for other repos such as Alien Bob or Robby Workman's the choice of how to track or update the packages used from their repos is left up to the user.  It is this choice that really forces the user to learn linux's tools such as rsync, wget, cron, bash scripting, etc.  For example you might choose to mirror the repo and use a cron job to look for updates to their changelogs, then use the default Slackware tools to update accordingly.  It is at this point you are not using a particular distros package manager to do the work for you you need to learn how to do it yourself to make it as easy as you wish.  You are not relying on APT or Yum to start needed (or uneeded) services upon an installation of a package you need to understand what services need to be started and set them to do so.

As for documentation the official set is included right in your DVD medium and housed on the official repos.  There are a set of README and How-To text files that provide you the official documentation set.  There is documentation on installation, changes and hints, LVM setup, encryption setup, RAID setup, creating an initrd to use the generic kernel, and others.  This is the consolidated documentation set you were looking for.  In addition to that there is a print and online book called Slackware Linux Essentials which provides more in-depth information although is in need of an update.  Also there is the community maintained Slackwiki and then of course the comprehensive linux links on the LQ forums which has links to everything noted above and more.

As for the software provided at installation, yes there is quite a selection of software.  The Slackware way is to give you a working functional workstation or server right out of the box.  Slackware does not assume what you want it merely gives you the official package set and lets you decide what you want from it.  You can easily modify what packages you do or do not want at installation time.   One example is if you do not want the KDE desktop just unselect it from the installation menu.  Slackware assumes you know what you are doing and will gladly let you uninstall any package whether or not you might want or need it later this is why the regulars on the LQ forums recommend that new users to Slackware do the full install as this provides all necessary packages, tools and dependancies.

Anyway as you see I could go on and on as I am a huge Slackware fan.  I started out with Linux a couple years ago using Ubuntu, Debian, Fedora, openSUSE, and was unsatisfied.  I was listening to the Linux Reality Podcasts by Chess Griffin and he did two shows almost exclusively on Slackware and I was extremely intrigued by it and you could really sense the passion he had for it.  I finally got an intel machine and tried 12.1 or 12.2, got it installed but the learning curve was too steep for me at that time.  I remember not knowing how to edit a config file using the command line and just not getting it at all.  Did some distro-hopping and kept coming back every so often to Slackware, each time I would learn a little more about linux.  By the time 13.1 rolled around I was hooked and had became a DVD subscriber.  I hope you give it another shot and below are links to all of the stuff mentioned above.

Slackware official readmes and how-to's:
[http://slackware.osuosl.org/slackware-13.37/]("http://slackware.osuosl.org/slackware-13.37/")

Slackbuilds.org:
[http://slackbuilds.org/]("http://slackbuilds.org/")

sbopkg:
[http://www.sbopkg.org/]("http://www.sbopkg.org/")

Slackware Linux Essentials:
[http://www.slackbook.org/html/index.htm]("http://www.slackbook.org/html/index.htm")l

Alien Bob's wiki:
[http://alien.slackbook.org/dokuwiki/doku.php]("http://alien.slackbook.org/dokuwiki/doku.php")

Robby Workman's packages:
[http://rlworkman.net/pkgs/]("http://rlworkman.net/pkgs/")

LQ Forums Slackware Linux Links:
[http://wiki.linuxquestions.org/wiki/Slackware-Links]("http://wiki.linuxquestions.org/wiki/Slackware-Links")

gnomeslackbuilds.org:
[http://gnomeslackbuild.org/]("http://gnomeslackbuild.org/")

Wow that post must have taken quite a while!  Thank you!

I'll try Slackware again.  Perhaps I'm like you, it's maybe too much for me right now.

Thanks also to everyone else who posted their experiences with Slackware.  I think it's because I didn't spend time to really get into the nitty-gritty of it - for example, I never managed to install a package, I just looked at the dozen or so ways I could do it and got confused.

---

### Post by andrew.46 on 2011-05-06
> **tgalati4 said:**
> Also because slackware was conceived, developed, and assembled by one person (Paul V.)....

Or perhaps *Patrick* V....

---

### Post by boydrice on 2011-05-06
> **3Miro said:**
> I was impressed by how smooth Slackware KDE implementation was. 

You can get the latest KDE usually from Alien Bob's Ktown repo [http://alien.slackbook.org/ktown/]("http://alien.slackbook.org/ktown/")

> **3Miro said:**
> The XFCE spin becomes a tweaked version of Gnome. Not on Slackware.

You can also get Xfce 4.8 from Robby Workman's repo [http://connie.slackware.com/~rworkman/xfce-4.8/]("http://connie.slackware.com/~rworkman/xfce-4.8/")

> **3Miro said:**
> I guess I will have to check sbopkg, this may be the thing that I am missing.
sbopkg also has queue files, which you can "automate" a large number of builds with their deps in order.  I have one as a post-install script that I save after an install, open a terminal as root then just sbopkg -i post-install.sqf.  
[http://www.sbopkg.org/queues]("http://www.sbopkg.org/queues")

---

