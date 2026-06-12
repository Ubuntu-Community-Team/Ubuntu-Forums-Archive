---
title: "Can I restore network settings from the Ubuntu install CD ??"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-01-07
Don't ask me how but I deleted some of the network settings (can't remember which ones), including host name, and some others that were installed during installation from the CD for Ubuntu 6.06.1. During the install I was connected to the internet via ethernet connection thru my Belkin wireless router (used as access point for home network). The install recognized the connection and configured it perfectly, so no problems there. I was trying set up my T-Mobile internet card a Sony Ericcson GC89, and got nowhere due to the card not being supported by T-Mobile for linux. I am trying to use ndswrapper but can't do it until I have an internet connection. I have a Toshiba Satellite Pro 768 Megs RAM--40Gig HD with dual boot (Windowz XP and Ubuntu 6.06.1) I am on the internet now with windoz. Just wondering if the network settings can be re-installed from the CD without having to do a complete install or rescue install? Can't I just download the network manager from the CD? Thanks for the help and sorry for the long post--Just lost big time and am learning little by little. By the way I am on the road now using the GC89 card now and have no ethernet connection until I return home in about a week and a half.

---

### Post by scrooge_74 on 2007-01-07
Put the CD in the PC and use synaptic if you feel that will get things repair.

the hostname of your computer is in /etc/hostname

---

### Post by jerrynewt on 2007-01-07
Thanks for the tip-I'll give it a try. I have to reboot into Ubuntu to try, so be back in a while and let you know how it goes.

---

### Post by jerrynewt on 2007-01-07
OK I'm back but I can't run any administrative functions. What gives on that?? I tried to run network manager--nothing--synaptic package manager--nothing, all admin apps will not run. Can I copy the apps to my desktop and instqall them from there or do I have a deeper problem not being able to run admin apps?

---

### Post by scrooge_74 on 2007-01-07
open a terminal and do gksudo the_name_if_the_app  and check for error messages.

try gksudo synaptic

maybe you broke something  and may have to reinstall your system

---

### Post by jerrynewt on 2007-01-07
Ok tried to run the gksudo command and got "sudo: unable to lookup (none) via gethostbyname ()". Guess I messed things up pretty bad. Any ideas or will I have to reinstall from scratch?

---

