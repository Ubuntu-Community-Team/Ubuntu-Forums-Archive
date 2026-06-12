---
title: "Very HAPPY newbie!! ...with couple of questions..."
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by xcafeus on 2007-10-15
Hi every1,

Great job! I mean the effort you guys put into this project is unbelievable! I just finished installing Feisty in dual boot mode with Windows XP under raid0. I followed the FakeRAID howto guide and tried it around 5 times until I got it right!... I even had to install ubuntu-desktop from command line in "recovery mode" because it failed while I was following the guide. AND IT WORKS!!! Im so happy (although I almost reached the point of going crazy).

It was about time to start using Linux and hopefully one day Ill be able to help others!

The problems I got at the moment are the following:

1) There is no "Restricted drivers" menu under "System-Administration" or anywhere else. So I cannot do any "nvidia" stuff (beryl and so on). I got a 6800 vanilla.

2) My stupid Linksys Wifi 54G PCI card is found but not working and I keep seeing a "microcode blah blah" error for the chipset. My Netgear WG111v2 USB adapter works but ONLY in WEP mode not WAP Personal.

3) Although my Soundblaster Live! is found and working with LiveCD it does not work when booting from HDD. It is also shown in Hardware Information but thats about it. I get error message "No volume control GStreamer plugins and/or devices found"

The PC is a P4, 3GHz, 1GB ram.

Any help is appreciated. Even howto's.. Please use as much detail as your time and mood allows...

Keep up the good work.

Thank you in advance,
George

---

### Post by Kosimo on 2007-10-15
Welcome to the Ubuntu world :)

Just a quick question.
Witch version of Ubuntu are you currently using?

Ubuntu Gutsy gibbon 7.10 is going to be released in 3 days and It have much more hardware compatibility than Feisty 7.04

---

### Post by Pumalite on 2007-10-15
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

### Post by Kosimo on 2007-10-15
OOoopss

Sorry, I just realized that you're using Feisty..

How about try the Release Candidate of Gutsy witch is already available here:

[http://www.ubuntu.com/news/ubuntu-7.10rc](http://www.ubuntu.com/news/ubuntu-7.10rc)

---

### Post by Pumalite on 2007-10-15
Sound:

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)

Wireless:

[http://www.linux.com/feature/56946](http://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuidep://www.linux.com/feature/56946)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion](https://help.ubuntu.com/community/WifiDocs/WirelessCardsByVersion)

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by xcafeus on 2007-10-15
oh man! you guys are fast! ...regarding 7.10 I think Ill wait just a little while since I JUST MANAGED to get 7.04 up and running especially under raid0 it wasnt very easy for me (I never used linux before)...so Im afraid Ill mess it up by going to 7.10 especially a pre-release version - thanks for the tip regarding hardware compatability Ill surely test it in the near future... Pumalite thanks for the links Ill start reading... :)

---

### Post by xcafeus on 2007-10-15
unfortunately I keep finding new things that dont seem to be right.. There is no "Software sourses" shortcut, no "Synaptic Package Manager" and when I tick them in "Main Menu" they untick themselves a second later... ooops..

---

### Post by xcafeus on 2007-10-15
yeah baby! after doing some "sudo" work I enabled my user - that is myself to have sound, perform administrative tasks etc... nvidia is now ok - sound is ok. the stupid WiFi card still give me trouble but Ill deal with that tommorow.

nite.

---

### Post by bobpur on 2007-10-15
FYI- If you get the latest Release Candidate of Gutsy Gibbon v7.10 now, you'll already have it installed and running when it is finally released. All you have to do then is maintain the updates and you'll have the same distro already that everyone else will be crowding the servers to get in a few days.

                                             Good Luck.

---

### Post by xcafeus on 2007-10-16
> **bobpur said:**
> FYI- If you get the latest Release Candidate of Gutsy Gibbon v7.10 now, you'll already have it installed and running when it is finally released. All you have to do then is maintain the updates and you'll have the same distro already that everyone else will be crowding the servers to get in a few days.

                                             Good Luck.

that sounds right... Ill try to find info on how to upgrade without messing things up.. thanks again. =D>

---

### Post by Joeb454 on 2007-10-16
I think it's just a case of running ```
sudo update-manager -d
``` from the terminal.

Somebody correct me if I'm wrong

---

### Post by bobpur on 2007-10-16
sudo apt-get dist-upgrade

I think that will work from "Fiesty." Also, I believe that Synaptic has a "Full Upgrade" button when a new Ubuntu version comes along. However, I have been wrong before as my wife takes great delight in pointing out:)

---

### Post by xcafeus on 2007-10-16
unfortunately the upgrade killed my installation since it is Raid0 UNAWARE...

[http://ubuntuforums.org/showthread.php?t=575632&highlight=upgrade+to+gutsy&page=5](http://ubuntuforums.org/showthread.php?t=575632&highlight=upgrade+to+gutsy&page=5)

a bit unhappy at the moment... too much time wasted. I have to start over now. NO IM NOT GIVING UP Im just a little pissed off.

---

### Post by xcafeus on 2007-10-16
ok now I fixed it... I had to download 7.10rc, boot with LiveCD, follow the Fakeraid guide from the part the "mount" stuff begins and install DMRAID, reconfigure GRUB, rewrite menu.lstentries with respect to the raid devices (/dev/mapper/isw_...). After that I managed to boot into 7.10 without problems! BUT why should I have to go through that? Thats the question. Maybe because like this I learn more.

Anyways up and running again.

---

### Post by neuralnet on 2007-11-12
Thanks xcafeus, sorry you had a hard time but you saved me (&other too I'll bet) from screwing up their fakeraid setups.. It really should configure the menu.lst file properly during the upgrade.. Why not I wonder ?

---

### Post by Pumalite on 2007-11-12
You guys should stay away from upgrades and stick to clean installs.

---

