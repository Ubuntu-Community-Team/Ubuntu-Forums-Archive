---
title: "ubuntu + beryl"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by crashadder on 2007-09-23
Hi there,
I am completely new to linux and ubuntu. I work as a systems and network administrator in a multinational company where everything has to be MS..I saw a video on youtube presenting the amazing 3d effects in ubuntu+beryl. I then downloaded and installed ubuntu 7.04 on vmware. I somehow managed to install beryl as well. But i cant see any effects whatsoever. I have a dell D620 latitude laptop with nvidia graphics card. I want to make it dual boot with win xp and ubuntu. Where should i start ? I seriously have no idea..I am ready to format the entire hdd. Should i install ubuntu first ? how should the partitions be made ? Guide me please

---

### Post by staticvoid on 2007-09-23
hey man,
1. Instead of Beryl, use compiz-fusion
2. install windows first, then get the "alternate" ubuntu desktop cd. Go through the partitioning steps manuelly you should have:

512 mb - 1gb of "swap"
then the rest should be "/" 

thats the simplest setup. windows automatically partions your drive into "C" and "D". You can format your D drive and then go from there...installing the operatin system there.

You can find how to do bothe steps 1 and 2 in detail here:
1. [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) 
2. [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

you can google for more info on partitioning.

partioning is perty tricky no matter how simple it may sound. BACK YOUR DATA.

feel free to PM me :D,

Static Void

---

### Post by SOULRiDER on 2007-09-23
To install the NVidia Drivers once Ubuntu is installed follow this link:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Also, as staticvoid mention, you should use Compiz-fusion, its newer than beryl and it provides more functionality as well as better performance. for a guide on how to install it visit this link:
[http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367)

---

### Post by staticvoid on 2007-09-24
Take SOULRiDER links and my dual boot link. You need to get NVidia drivers...yes indeed. Sorry I over looked that ;)

SV

---

