---
title: "Installing ECI ADSL modem driver"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by JohnnyMarr on 2006-02-11
Hi could someone help me, or give me advice on installing the ECI ADSL driver on UBUNTU v.5.10, the driver is a Linux driver for ECI HiFocus ADSL USB
and Globespan based modems. My modem is the BT voyager 105. I managed to install it, and get it running before on fedora 4, but after switching from fedora to ubuntu im fairly clueless. Ive read the wiki concerning winmodems etc and ive found nothing helpful, just a link to a site that dosent even list my modems chipset. Anyway on the download section of eciadsl they list the different usermodes for different distros, suse, mandriva, fedora etc but nothing concerning ubuntu, heres a link. [http://eciadsl.flashtux.org/download.php?lang=en](http://eciadsl.flashtux.org/download.php?lang=en)

plus when i try to sudo dpkg the deb file  it some up with file not found which is annoying as i know ive typed the file name in correctly
Ive searched the forums and found people have got the driver installed, but nowhere does it say how :(. Im sorry for asking such newbish questions but im very new to linux and especialy ubuntu

---

### Post by sharke on 2006-02-12
The command is sudo  dpkg -i /home/enter your user name/eciadsl-usermode_0.11-1_i386.deb
This is if you downloaded to your home folder.
Regards
Sharke

---

### Post by SteveHoffmanUK on 2006-03-21
I have also been trying to install the eciadsl modem driver for the BT Voyager105 modem. I got this far and then got these messages:
> 
dpkg: dependency problems prevent configuration of eciadsl-usermode: 
eciadsl-usermode depends on pppoe; however: Package ppoe is not installed.
dpkg: error processing eciadsl-usermode (--install): dependency problems - leaving unconfigured
Errors were encountered while processing: eciadsl-usermode

I went to Synaptic Package Manager, and it shows that pppoeconf (Version 1.8ubuntu2) is installed. I guess there is a difference between ppoe and ppoeconf? How do I get ppoe and instal it?

---

### Post by Blondie on 2006-05-07
See my reply in this thread,
[http://www.ubuntuforums.org/showthread.php?t=171202](http://www.ubuntuforums.org/showthread.php?t=171202)

---

