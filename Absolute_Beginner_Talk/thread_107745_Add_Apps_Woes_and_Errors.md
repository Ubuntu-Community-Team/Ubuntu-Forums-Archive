---
title: "Add Apps Woes and Errors"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by filosofic on 2005-12-23
Hi,
I'm new to Linux and Ubuntu but really like what I see and can do so far.
I'm running a dual-boot Xp-Ubuntu on an HP Pavilion ze5300 laptop, 2.4...
When I go to Applications -> Add Applications -> File -> Advanced, which gets me into the Synaptic Package Manager, I get the following error message:

W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)[/SIZE][/SIZE]

I do like to mess around with many of the controls and in the terminal but I usually don't do anything that should mess things up that much.

Any suggestions?

It does not seem to affect the function of my laptop although I just lost control over the mouse, and I get error messages when I run the Frequency Monitor Preferences.

Thanks
Dave

---

### Post by filosofic on 2005-12-23
Hi again,
I think I may have figured out this for myself.
I'm running a 
sudo apt-get update
sudo apt-get upgrade

...and I don't know what it's doing but it's sure doing something :>

In retrospect this post shouldn't be in the Beginner Talk section, but I've only been at this for a couple of weeks.  My apologies.

---

### Post by dcast on 2005-12-23
The errors you posted were repository sites. Is your computer connected to the internet?

---

### Post by filosofic on 2005-12-23
Yes it is.  Through dsl and wireless.  I also have Firestarter running, but I must confess that I'm not that familiar with it as I'm used to running ZoneAlarm on XP.

---

### Post by filosofic on 2005-12-23
After update and upgrade everything seems to be working ok.

---

### Post by mendy on 2005-12-26
I have the same problem with the "couldn't stat etc." messages.
I ran sudo apt-get update and upgrade, and it didn't help.
Also I tried loading firestarter and I don't know where to find it to open it.

Any suggestions?

---

