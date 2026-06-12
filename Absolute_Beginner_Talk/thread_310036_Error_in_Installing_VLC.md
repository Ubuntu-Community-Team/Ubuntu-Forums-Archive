---
title: "Error in Installing VLC"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Jorigily on 2006-11-30
I have been trying for the last 2 days to fix this problem, but cant.:( 

when i type in sudo apt-get install vlc i get the following...

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _breezy Hedgehog_ - Release i386 (20050407) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fbreezy%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _breezy Hedgehog_ - Release i386 (20050407) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fbreezy%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package vlc

Any help on this matter will be greatly appreciated :D

---

### Post by apjone on 2006-11-30
could you post your /etc/apt/sources.list please

---

### Post by tronica on 2006-11-30
open your sources.list

> sudo gedit /etc/apt/sources.list

then comment out the cdrom witch should be the first listing

comment it out by adding one of # these in front of the line/s, save that and run > sudo apt-get update

---

