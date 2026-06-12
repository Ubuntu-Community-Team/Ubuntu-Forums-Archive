---
title: "Any Linux installer keeps freezing , I’m unable to install linux."
date: 2018-09-25
forum: Any Other OS
---

### Post by gameerik on 2018-09-25
It’s a bit if a long story but I will do my best as a beginner to explain everything.I had Ubuntu 17 and deceided to upgrade it to 18 via the command line command, after the update there was a weird bug which I couldn’t fix despite lookin for days on the internet. This weird bug , was that after pressing enter on the login screen  , ubuntu 18.04 would freeze completely .So I tried reinstalling it , which failed , since it kept freezing at different times (booting from liveUSB) .I restarted so many times (in hope of the installer to work) that the previous os got corrupted. That’s when I deceided to switch to a different linux distribution : linux mint. The same thing happened , except now I got a different message : “low disk space 0bytes remaining”.(note : I don’t have an OS so I fully boot from live USB). So I installed windows , to delete partitions , but it was weird , since I have an SSD of 256GB and only 238GB of maximum capacity was shown.Anyway after this , I tried linux installation 2 times, without and with liveUSB , but it failed with the same “no space” remaining message . Now I don’t have and OS , and booting from liveUSB (currently containing mint).

---

### Post by ajgreeny on 2018-09-25
From your live Mint USB run command ```
sudo fdisk -l
``` and report back here the output.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by k9r4n on 2018-12-05
Have you tried just deleting, and reformatting your SSD? Maybe there's something wrong with the SSD, like it bit be formatted in a way the OS cannot read it.

---

