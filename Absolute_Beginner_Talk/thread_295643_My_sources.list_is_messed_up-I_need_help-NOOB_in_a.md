---
title: "My sources.list is messed up-I need help-NOOB in action"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by kindafunnylookin on 2006-11-08
A message that comes up just about every time I use the automatic update follows. I am having problems installing certain things like flash 7 and 9 along with others that I can't remember right now and I wonder if the errors in my sources list could be the root of the problem. Any ideas would be appreciated.
Peter

```
W: Duplicate sources.list entry http://archive.ubuntu.com dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-security/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-security_main_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-security/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-security/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-security/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_restricted_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-updates/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_main_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_restricted_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_universe_binary-i386_Packages)
 W: Duplicate sources.list entry http://archive.ubuntu.com dapper-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_multiverse_binary-i386_Packages)

```

---

### Post by dannyboy79 on 2006-11-08
it's not the reason your having problems, it's simply telling you that you have duplicates of the same repo in your sources.list. why don't you do, sudo gedit /etc/apt/sources.list and review it line for line and whereever you see the duplicate entry either put a "#" at the front of that line or completely remove it, but be careful to only remove that 1 line. if your screen isn't big enough, it may word wrap, so just be careful waht you delete.

---

### Post by kindafunnylookin on 2006-11-08
Thanks for the reply. I'll do that and try to install Flash again.
Peter

---

### Post by kindafunnylookin on 2006-11-08
OK. I cleaned up my sources.list but I still cannot install Flash Player. I tried using Synaptic and the istall was going fine and just as it was finishing the terminal said 'Package not installed. I got the same result using automatix 2.
Peter

---

### Post by dannyboy79 on 2006-11-08
> **kindafunnylookin said:**
> OK. I cleaned up my sources.list but I still cannot install Flash Player. I tried using Synaptic and the istall was going fine and just as it was finishing the terminal said 'Package not installed. I got the same result using automatix 2.
Peter


sounds like a automatix problem, you should head over to their forums. you'll get much better support.

---

### Post by kindafunnylookin on 2006-11-08
Tks again
Peter

---

### Post by PriceChild on 2006-11-08
If the as you say, the package has downloaded, and it only fails on the one package then there's something else happenning.

Could you post the actual error here please? and also a copy of your sources.list.

You can always install flash manually also... (matter of downloading a zip, extracting, and moving a single file)

---

### Post by kindafunnylookin on 2006-11-08
I found it. All this time I've been installing to Firefox and looking in Swiftfox.
A real NOOB in action - hanging his head.
Thank you for your efforts to help the helpless:-D

---

