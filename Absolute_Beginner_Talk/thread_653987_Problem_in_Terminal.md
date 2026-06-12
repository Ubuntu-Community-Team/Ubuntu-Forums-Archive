---
title: "Problem in Terminal"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by TheNater on 2007-12-30
Hi guys This is my first time using Linux and I'm less than 48 hours into it.

Anyways, I'm having a problem trying to run *sudo apt-get update* 

Here's what I get...

nate@nate-desktop:~$ sudo apt-get update
[sudo] password for nate:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Fetched 1B in 5s (0B/s)  
[B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

Any suggestions?

n00b

---

### Post by b0rka7a on 2007-12-30
Are you using Synaptic or installing anything in a terminal when you type sudo apt-get update ?

Edit: I mean that you must not installing anything or using synaptic, update-manager, etc...

---

### Post by taurus on 2007-12-30
Do you happen to have synpatic, Add/Remove, or adept running?  If you do, you need to shut it down first before you can run apt-get from a terminal.

---

### Post by TheNater on 2007-12-30
Yeah Wow I feel like a noob. I had synaptic open as I was trying to uninstall Wine and then reinstall it in the terminal. Thanks guys

---

