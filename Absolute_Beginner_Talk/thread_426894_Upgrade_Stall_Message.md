---
title: "Upgrade Stall Message"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-04-28
I get this message when I try to upgrade from 6.10 to 7.04:

[http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

How can I fix that?

Caruso

---

### Post by carusoswi on 2007-04-29
So, am I alone in  experiencing this problem?

Caruso

---

### Post by mikeyphi on 2007-04-29
See if this helps: Open a terminal and enter
sudo apt-get upgrade

then
sudo apt-get dist-upgrade

---

### Post by Kobin on 2007-04-29
Do you have a firewall running that could be blocking the .bz2 files?

Otherwise try the following command and then do the upgrade again:

sudo apt-get clean
sudo apt-get update

---

### Post by Kobin on 2007-04-29
Maybe upgrading through the terminal will work, but the Ubuntu team recommends doing it through synaptic. They say you may have to fix more problems your self later if you do it through the commandline...

---

### Post by Kobin on 2007-04-29
Sorry, I mean updatemanager and not synaptic of course

---

### Post by mikeyphi on 2007-04-29
Seems someone else had this problem.....

[http://ubuntuforums.org/showthread.php?t=427256](http://ubuntuforums.org/showthread.php?t=427256)

---

### Post by carusoswi on 2007-04-29
Result from terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  fakeroot g++ g++-4.1 libc6-dev libstdc++6-4.1-dev opera
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_edgy-commercial_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


?????
Caruso

---

### Post by Kobin on 2007-04-30
which command did you run?

If you are using apt-get then just run the following again:

          sudo apt-get clean
then
          sudo apt-get update
then
          sudo apt-get upgrade
then 
          sudo apt-get dist-upgrade


Or did you already do this?
Still, I think it's better to do it using the update manager.....

---

