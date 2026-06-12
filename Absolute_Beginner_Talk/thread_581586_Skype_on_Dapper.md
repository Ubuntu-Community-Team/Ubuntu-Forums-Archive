---
title: "Skype on Dapper"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by klaasvanschelven on 2007-10-19
Hi all,

I'm trying to get skype to work on "Long Term Service" Dapper. It seems the people at Skype have no such conception of service, since their packages no longer work with the old Dapper libraries. Does anyone have an idea how I can get myself an old skype .deb file? I'm stuck with Dapper for now because none of the newer stuff will install on my system (I will probably rant about that when I finally have a working system).

$ sudo aptitude install skype
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  skype
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.4MB of archives. After unpacking 16.3MB will be used.
The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.12) but 1.0.10-2ubuntu4 is installed.
         Depends: libc6 (>= 2.3.6-6) but 2.3.6-0ubuntu20.5 is installed.
         Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is installed.
         Depends: libqt4-core (>= 4.2.1) but it is not installable
         Depends: libqt4-gui (>= 4.2.1) but it is not installable
         Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

---

### Post by linuxwizard on 2007-10-19
Look over this

[https://help.ubuntu.com/community/Skype?action=show&redirect=SkypeHowto](https://help.ubuntu.com/community/Skype?action=show&redirect=SkypeHowto)

---

### Post by klaasvanschelven on 2007-10-19
I did.

The problem is, quite specifically, that the libasound2 library doesn't go over 1.0.10 in Dapper, and the only currently available skype version needs 1.0.12 or greater. "Wizard" > I see that you're using Dapper. If you by any chance have the .deb packages for skype those would be appreciated very much.

---

### Post by linuxwizard on 2007-10-19
klaasvanschelven
I don't use Skype and I don't have of a deb package for you. I was doing some searching trying to find something that may help you. Look at the last post on this page. You might want to look into that. I hope this will help. Good Luck Dapper is my main system but also use Edgy & Feisty

[http://ubuntuforums.org/showthread.php?t=478600&highlight=skype+dapper](http://ubuntuforums.org/showthread.php?t=478600&highlight=skype+dapper)

---

