---
title: "Daemon Problem"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by czechman86 on 2007-12-16
A while back I posted a thread about programs randomly quitting and with the help of my cousin and some information on this forums, we discovered that the problem was with Madwifi, for it tainted my kernel. There was also one other problem, which I am having at the moment and was wondering if there were any known fixes for it. Sometimes programs will fail to open after I click on them and then the entire system will proceed to crash. My cousin told me again that this was due to Daemon errors, which are common in Debian based distros. Tonight, I had this problem and received an error message for the system that identified the problem as the following:

```
Process/usr/lib/gnome-control-center/gnome-settings-daemon received error signal 4
```

I believe that this is the root of all the problems, outside of the tainted kernel, that I have been having with my Ubuntu system. If anyone knows any fixes or any ways to further analyze it, your help would be greatly appreciated.

Thank you very much!

I posted this in the Apple Intel forum as I run Linux on a Macbook, but I thought also to post this in the starter forum as I am unfamiliar with Linux for the most part. I love Ubuntu and would love to keep it for my primary and only system, If anyone knows of any fixes for this problem, please post them. Thanks!

Other info about what I am experiencing. The problem appears to first start with firefox randomly quiting and then the rest of the system following suit. I have thought of maybe trying opera for a while to see if that would change things. Also, this problem happens every other boot up.

---

### Post by nowshining on 2007-12-16
do u have ALL UPDATES installed? and are u up to date on em'?

---

### Post by czechman86 on 2007-12-16
My system is 100% up to date.

---

### Post by llamakc on 2007-12-16
I've used Debian since for seven years and I've never heard any such thing as "daemon errors" being common.

Are you running with any add-ons/extensions for Firefox? Perhaps one of them has a leak, which leads to the instability of your system. If not that, I would boot into memtest from the GRUB menu and check the RAM.

---

### Post by czechman86 on 2007-12-16
> **llamakc said:**
> I've used Debian since for seven years and I've never heard any such thing as "daemon errors" being common.

Are you running with any add-ons/extensions for Firefox? Perhaps one of them has a leak, which leads to the instability of your system. If not that, I would boot into memtest from the GRUB menu and check the RAM.

I use adblock plus and the download status bar, but have read of no problems regarding those. this is a strange problem i know, and it seems as though i am the only one who is having it. i wish i could get to the bottom of things, as it is annoying to work with. when i ram test, what will i be looking for that might be able to provide answers? thanks!

---

### Post by LinuxGuy1234 on 2007-12-16
> **czechman86 said:**
> A while back I posted a thread about programs randomly quitting and with the help of my cousin and some information on this forums, we discovered that the problem was with Madwifi, for it tainted my kernel. There was also one other problem, which I am having at the moment and was wondering if there were any known fixes for it. Sometimes programs will fail to open after I click on them and then the entire system will proceed to crash. My cousin told me again that this was due to Daemon errors, which are common in Debian based distros. Tonight, I had this problem and received an error message for the system that identified the problem as the following:

```
Process/usr/lib/gnome-control-center/gnome-settings-daemon received error signal 4
```

I believe that this is the root of all the problems, outside of the tainted kernel, that I have been having with my Ubuntu system. If anyone knows any fixes or any ways to further analyze it, your help would be greatly appreciated.

Thank you very much!

I posted this in the Apple Intel forum as I run Linux on a Macbook, but I thought also to post this in the starter forum as I am unfamiliar with Linux for the most part. I love Ubuntu and would love to keep it for my primary and only system, If anyone knows of any fixes for this problem, please post them. Thanks!

Other info about what I am experiencing. The problem appears to first start with firefox randomly quiting and then the rest of the system following suit. I have thought of maybe trying opera for a while to see if that would change things. Also, this problem happens every other boot up.

From reading:
1. The cause is GNOME. Solving: Remove ubuntu-desktop and install xubuntu-desktop.
or (if you keep GNOME):
2. Delete .gnome2_private, .gnome2, .gconf and .gconfd from your home directory. After this log out and log back in. The error will be then gone.

---

### Post by nowshining on 2007-12-16
.gconf and gconfd will delete the user prefs, themes, etc... at most make a backup of em first before deletion,

ctrl + h in the home folder to view hidden dot files.

---

### Post by czechman86 on 2007-12-16
> **nowshining said:**
> .gconf and gconfd will delete the user prefs, themes, etc... at most make a backup of em first before deletion,

ctrl + h in the home folder to view hidden dot files.

i really have no plans to delete my gconfd file or any other file out of my home directory as of yet, however, it is interesting that this may be a problem related to gnome. for alternatives i am looking at xubuntu, but would like to keep ubuntu if possible. thanks for the tips so far guys!

---

### Post by nowshining on 2007-12-16
.gconf and .gconfd contain the configuration (gconf-editor) settings.

---

### Post by nowshining on 2007-12-16
welcome, but it would of just defaulted to the default settings actually..

---

### Post by czechman86 on 2007-12-16
> **nowshining said:**
> welcome, but it would of just defaulted to the default settings actually..

so if i do delete those files, it will just return the default gnome settings? will that cause my wifi to die out or anything (i had to add drivers myself)?

---

### Post by czechman86 on 2007-12-16
> 
From reading:
1. The cause is GNOME. Solving: Remove ubuntu-desktop and install xubuntu-desktop.
or (if you keep GNOME):
2. Delete .gnome2_private, .gnome2, .gconf and .gconfd from your home directory. After this log out and log back in. The error will be then gone.

Could you also install KDE and not have this problem?

---

### Post by LinuxGuy1234 on 2008-02-09
> **czechman86 said:**
> Could you also install KDE and not have this problem?

Yes.

---

