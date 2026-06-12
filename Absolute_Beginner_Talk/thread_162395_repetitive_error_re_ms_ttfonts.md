---
title: "repetitive error re ms ttfonts"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-04-18
Please, I need some advice.  I keep getting the same error now when downloading various programs,  the most recent being the game 'scrabble'.  The error in synaptic is:

E: msttcorefonts: subprocess post-installation script returned error exit status 1

This seems to have started after I had changed from Firefox 1.07 (or whatever the version is on the Shipit CD) to 1.5.  I know the terminal shows multiple attempts to find the msttfonts while loading software but never finds it.  Is this a common issue?
Thanks.

---

### Post by hw-tph on 2006-04-19
The msttcorefonts package is in the multiverse repositories. If you are unsure how to enable multiverse, [refer to the wiki](https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu).


Håkan

---

### Post by flyingsolo on 2006-04-19
Thanks but when I open Synaptic to choose msttcorefonts, it is marked as already installed.  I tried reinstalling and got the same error I originally quoted above.

E: msttcorefonts: subprocess post-installation script returned error exit status 1

I also get the warning as follows on opening Synaptic:

W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)

I'm quite new at this so help is appreciated.  Am I heading to a reinstall of OS?
Thanks again

---

### Post by hw-tph on 2006-04-19
[QUOTE=flyingsolo]Am I heading to a reinstall of OS?[/QUOTE]

Most likely not. Open a terminal and type **sudo apt-get update** and see if that helps. It should refresh your local package listings.


Håkan

---

### Post by flyingsolo on 2006-04-19
Thanks again.  I'll need to try this later since now I'm at work and Ubuntu machine is home.

---

