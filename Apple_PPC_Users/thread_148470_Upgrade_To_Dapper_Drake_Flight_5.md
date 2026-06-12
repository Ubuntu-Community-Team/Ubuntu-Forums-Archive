---
title: "Upgrade To Dapper Drake Flight 5"
date: 2006-03-22
forum: Apple PPC Users
---

### Post by fraterf93 on 2006-03-22
I'm running Kubuntu 5.10 on my iMac G3 600 MHz, and was wondering how to upgrade to Dapper Drake Flight 5 without wiping my partitions and starting fresh.

---

### Post by markr on 2006-03-22
I believe you just change your sources.list from breezy to dapper,  do an upgrade and sit back.

---

### Post by fraterf93 on 2006-03-22
OK great thanks!  Now how do I do that?  Obviously I'm a n00b!;)  Do you edit the file with nano?  Im gonna reboot into kubuntu.  brb

---

### Post by nocturn on 2006-03-22
When dapper releases, there should also be an update to upgrade-manager on Breezy.

This new version will show the new stable release and allow you to upgrade.

---

### Post by fraterf93 on 2006-03-22
nocturn, that's great and all, but I want to test the Dapper Flight 5 PPC version on my machine to see if the bugs have been worked out and offer my input so they can be fixed for the final release.  There were some issues with the video card in Breezy 5.10.  It would freeze at login, and had to edit etc/modules, and the xorg.conf to get it to work.

---

### Post by cosborn72 on 2006-05-09
I haven't tested this on my PPC machine, only on a PC, so take this with a grain of salt.  You may want to verify that your sources.list in in this directory.

Make a copy of your sources list.
 
cp /etc/apt/sources.list /etc/apt/sources2.list

Open /etc/apt/sources.list with a editor 

sudo nano /etc/apt/sources.list

Change every instance of breezy to dapper  (if you are uncomfortable with the command line, you can do this in synaptic as well.  Go to the respository section and change all instances of breezy to dapper.)

close and run the following command.

sudo apt-get dist-upgrade

That should do it.

Note of warning- the PPC version of dapper has been pretty buggy for me.

---

### Post by cjazz on 2006-05-12
[QUOTE=cosborn72]I haven't tested this on my PPC machine, only on a PC, so take this with a grain of salt.  You may want to verify that your sources.list in in this directory.

Make a copy of your sources list.
 
cp /etc/apt/sources.list /etc/apt/sources2.list

Open /etc/apt/sources.list with a editor 

sudo nano /etc/apt/sources.list

Change every instance of breezy to dapper  (if you are uncomfortable with the command line, you can do this in synaptic as well.  Go to the respository section and change all instances of breezy to dapper.)

close and run the following command.

sudo apt-get dist-upgrade

That should do it.

Note of warning- the PPC version of dapper has been pretty buggy for me.[/QUOTE]


One additional step: do
sudo apt-get update
before sudo apt-get dist-upgrade

---

### Post by fraterf93 on 2006-05-15
Thx Guys, I did all that and Dapper is totally unusable on my iMac G3 600.  I've tried Dapper live CDs(they dont boot properly), and text mode CDs of Ubuntu, Kubuntu, and Xubuntu.  I get the same results that I got with the dist-upgrade.  A totally unusable iMac.  I get the same problem that I got when I first installed Breezy, but the fix provided here :[http://www.ubuntuforums.org/showthread.php?t=89712]("http://www.ubuntuforums.org/showthread.php?t=89712") does not fix the problem.  As a matter of fact, when I dist-upgrade these settings are unchanged, and yet I still get the same "login freeze."  Please I hope these are fixed before Dapper comes out.  It would suck to not be able to use it on this machine.  Especially Xubuntu, with it's claim to be perfect for older hardware. 
    

    As a side note Dapper installs, and runs fine from text mode CD (Ubuntu, Kubuntu, or Xubuntu) on my 1.25 Mac mini.  I even got Mac-On-Linux running!  The mini will boot from live CDs but the installer crashes.

Thx again!

---

