---
title: "Synaptic Problem"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by dead_man_walking on 2006-03-30
Hi guys.... When i try running synaptic i get this error
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

After theese errors synaptic starts but i cant download  " rar " can anybody help me out pls

---

### Post by WoodyMahan on 2006-03-30
Synaptic runs off of a file called sources.list.  FIrst backup your sources.list file by opening the terminal and entering:
sudo cp /etc/apt/sources.list /etc/apt/backupofsources.list

Then Open the sources.list:
sudo gedit /etc/apt/sources.list

Highlight everything and deleted it all.  Save.

Open Synaptic and hit the Refresh Button.  (It should come up empty).

Re-open the sources.list using the command above and copy/paste this into it:

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

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

deb [http://theli.free.fr/packages/breezy/](http://theli.free.fr/packages/breezy/) ./
## created by arnielistenadded




Click Save.

Re-open SYnaptic and thins should be working.

---

### Post by Mustard on 2006-03-30
The error in the opening post could possibly be solved by hitting the 'Reload' button, after the error messages comes up.

---

### Post by dead_man_walking on 2006-03-30
thanx guys ... it was really so nice of you !!!...it works and i now i can download rar
can u guys let me know of a site which has tuts or things which can help me run ubuntu properly ....thanx for ur help again ...i am really new to linux

---

### Post by WoodyMahan on 2006-03-30
I learned right here.  Try something, break it, try again, post a question on the forum.  I also tool around on the forums a lot and read posts that look interesting or seem to address something I might want.  I'm by no means a guru, but I am functioning pretty handily now.

Here are some sites I got from SD-Plissken:
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[http://www.perpetualpc.net/srtd_commands_rev.html](http://www.perpetualpc.net/srtd_commands_rev.html)


It is always helpful to understand the command window.

---

### Post by Mustard on 2006-03-30
[QUOTE=dead_man_walking]thanx guys ... it was really so nice of you !!!...it works and i now i can download rar
can u guys let me know of a site which has tuts or things which can help me run ubuntu properly ....thanx for ur help again ...i am really new to linux[/QUOTE]

Try this one...

[http://ubuntuforums.org/showthread.php?t=142716](http://ubuntuforums.org/showthread.php?t=142716)

---

### Post by WoodyMahan on 2006-03-30
[QUOTE=Mustard]Try this one...

[http://ubuntuforums.org/showthread.php?t=142716](http://ubuntuforums.org/showthread.php?t=142716)[/QUOTE]


Good Link Mustartd.  I'm sending this one to my Dad.

---

