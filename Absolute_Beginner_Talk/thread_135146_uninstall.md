---
title: "uninstall?"
date: 2006-02-23
forum: Absolute Beginner Talk
---

### Post by StageMgr2Stars on 2006-02-23
So I installed blindkeys and and now it won't let me use my arrow keys... how do I uninstall that. I cant find it in the applications menu anywhere.

---

### Post by bluevoodoo1 on 2006-02-23
How did you install it?

---

### Post by StageMgr2Stars on 2006-02-23
with the apt get thing...


I'm still a n00b with most things.

---

### Post by bluevoodoo1 on 2006-02-23
how about...

```

sudo apt-get remove blindkeys

```

---

### Post by StageMgr2Stars on 2006-02-23
courtneyscott@courtneyscott:~$ sudo apt-get remove blindkeys
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package blindkeys




That was what I got....

---

### Post by bluevoodoo1 on 2006-02-23
I don't see "blindkeys" in Synaptic. Is that the correct title? 

Try running, as was mentioned... ```
sudo apt-get update
``` and see if it can find the packages.

---

### Post by StageMgr2Stars on 2006-02-23
it was xbindkeys. but because my up arrow wasnt working I couldnt scan my recent commands. all is fixed now.

---

### Post by bluevoodoo1 on 2006-02-23
ah ha, xbindkeys. :)

---

