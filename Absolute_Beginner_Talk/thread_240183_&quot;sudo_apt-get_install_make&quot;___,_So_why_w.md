---
title: "&quot;sudo apt-get install make&quot;   , So why wont it install.??"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-08-20
> jason@Hp-Vectra-VL:~$ sudo apt-get install make
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://eyagi.bpa.nu](http://eyagi.bpa.nu) breezy/main Packages (/var/lib/apt/lists/eyagi.bpa.nu_%7ejamie_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://eyagi.bpa.nu](http://eyagi.bpa.nu) breezy/restricted Packages (/var/lib/apt/lists/eyagi.bpa.nu_%7ejamie_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://eyagi.bpa.nu](http://eyagi.bpa.nu) breezy/universe Packages (/var/lib/apt/lists/eyagi.bpa.nu_%7ejamie_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://eyagi.bpa.nu](http://eyagi.bpa.nu) breezy/multiverse Packages (/var/lib/apt/lists/eyagi.bpa.nu_%7ejamie_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://eyagi.bpa.nu](http://eyagi.bpa.nu) sarge/main Packages (/var/lib/apt/lists/eyagi.bpa.nu_%7ejamie_debian_dists_sarge_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://eyagi.bpa.nu](http://eyagi.bpa.nu) sarge/contrib Packages (/var/lib/apt/lists/eyagi.bpa.nu_%7ejamie_debian_dists_sarge_contrib_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://eyagi.bpa.nu](http://eyagi.bpa.nu) sarge/non-free Packages (/var/lib/apt/lists/eyagi.bpa.nu_%7ejamie_debian_dists_sarge_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package make
jason@Hp-Vectra-VL:~$



I have already run "sudo update" ](*,)

---

### Post by jimmygoon on 2006-08-20
You're internet is messed up... That or all those mirrors are down :S If you are at a hotel where you have to open firefox and accept the terms before you are really on the internet then you will have to do that... and then do the terminal work... like, try now...

---

### Post by jason.b.c on 2006-08-20
> **jimmygoon said:**
> You're internet is messed up... That or all those mirrors are down :S If you are at a hotel where you have to open firefox and accept the terms before you are really on the internet then you will have to do that... and then do the terminal work... like, try now...

[SIZE="3"]What...???[/SIZE]

In a hotel...???

---

### Post by jason.b.c on 2006-08-20
Alright , How do i clean up old sources.list backup's...???

---

### Post by digby on 2006-08-20
> **jason.b.c said:**
> I have already run "sudo update" ](*,)
By that, did you mean 'sudo apt-get update'?  Because with working internet, I'd expect that to fix it.  Otherwise, can you post your /etc/apt/sources.list?

---

### Post by jason.b.c on 2006-08-20
> **digby said:**
> By that, did you mean 'sudo apt-get update'?  Because with working internet, I'd expect that to fix it.  Otherwise, can you post your /etc/apt/sources.list?

Yes of cource i did , i'm not an idiot..!   

I'm just too lazy to type out the whole thing sometimes...

Anyway how do i cleanup my sources backups..???

---

### Post by nalmeth on 2006-08-20
What kind of internet connection are you using?? Looks like connection problem. Are you posting from the Ubuntu machine??

BTW, you should just install the build-essential package, it contains make and other useful tools.

---

