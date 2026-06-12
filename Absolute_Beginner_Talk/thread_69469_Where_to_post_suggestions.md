---
title: "Where to post suggestions"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by T Braun on 2005-09-27
I started using Ubuntu because I can easily upgrade to a new version. When a new version of Gnome comes out, I don't have to wait for months for a new version to be supported. I would like to see some installation changes to support frequent upgrades, for example from Breezy to Dapper. I was wondering where would be a good place to post suggestions?

Thanks
\t

---

### Post by BoyOfDestiny on 2005-09-27
[QUOTE=T Braun]I started using Ubuntu because I can easily upgrade to a new version. When a new version of Gnome comes out, I don't have to wait for months for a new version to be supported. I would like to see some installation changes to support frequent upgrades, for example from Breezy to Dapper. I was wondering where would be a good place to post suggestions?

Thanks
\t[/QUOTE]

If you mean upgrading from cd:
Hmm, if you choose manual partition, instead of the erase entire disk option, it will install that "on top" without losing yoru data. 

The other option (more tedious I think, but if you don't want to reboot) is to gedit etc/apt/sources.list and add the cdrom as a repository.

If you mean upgrading online:
edit your etc/apt/sources.list, and replace every instance of hoary with breezy (for example). A quick find and replace with gedit will do the job.

Granted this isn't very friendly for newbies...not too hard, but it would be nice if there was an easier option (maybe a little script) I suppose you can try posting in development relase forums, and go from there.

---

### Post by matthewv on 2005-09-27
I've never found any mention of this, but when I wanted to upgrade from Hoary to Breezy preview release, I burned the install ISO, and then, when I put the cd in my drive, Ubuntu just told me that the CD contained upgradeable packages (or something like that) and allowed me to upgrade from that. I didn't, but is it possible to just upgrade like that??

---

