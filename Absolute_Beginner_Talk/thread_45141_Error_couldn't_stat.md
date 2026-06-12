---
title: "Error couldn't stat"
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by Nopposan on 2005-06-28
I get the following message whenever I update my operating system or search for anything using the Synaptic package manager.

"W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)"

Can anyone tell me if this is important.  If it is important, then how do I correct it?  If it iis not important, then how do I avoid getting these messages?

Thanks.

---

### Post by sonny on 2005-06-29
well that usually means that the ftp has some problems, the only bad thing is that you can't get the package from that repositories, but apart of it everything sould be working. I don't get the same message, mine says something about the md5sum.

---

### Post by Nopposan on 2005-06-30
Alright, but I think maybe this ftp that Ubuntu Linux can't stat is important for Mozilla Firefox.  Here's the message I get when I try to run updates in the Ubuntu Update manager:
"It is not possible to upgrade all packages.

This means that besides the actual upgrade of the packages some further action (such as installing or removing packages) is required. Please use Synaptic "Smart Upgrade" or "apt-get dist-upgrade" to fix the situation.

The following packages are not upgraded:

mozilla-firefox
mozilla-firefox-gnome-support"

I think I was already using the "Smart Upgrade" option, and I don't understand why using either of these options will be helpful.  I'll try out the apt-get dist-upgrade thing and report back.

Thanks for your willingness to help though.

---

### Post by poofyhairguy on 2005-07-01
[QUOTE=Nopposan]Alright, but I think maybe this ftp that Ubuntu Linux can't stat is important for Mozilla Firefox.  Here's the message I get when I try to run updates in the Ubuntu Update manager:
"It is not possible to upgrade all packages.

This means that besides the actual upgrade of the packages some further action (such as installing or removing packages) is required. Please use Synaptic "Smart Upgrade" or "apt-get dist-upgrade" to fix the situation.

The following packages are not upgraded:

mozilla-firefox
mozilla-firefox-gnome-support"
[/QUOTE]

Thats means it wants you to close firefox so it can upgrade it.

---

### Post by Nopposan on 2005-08-27
Thank you, phg.

The firefox thing is history now.  However, I still get that annoying message "couldn't stat" that I got before; how can I stop the update manager and package manager from "stat"-ing the package in the first place?

---

### Post by RastaMahata on 2005-08-27
heh... It's been told a lot of times already: dont use marillat, it will break your ubuntu (its designed for pure debian). Use backports and backports-extra instead. [How to add all the extra repositories](www.ubuntuguide.org/#extrarepositories)

---

