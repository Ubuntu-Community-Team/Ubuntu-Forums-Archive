---
title: "apple isight recognition issues"
date: 2011-04-11
forum: Apple Hardware Users
---

### Post by shmibs on 2011-04-11
ohithur
over the past week or so i have been attempting, off and on, to get the built in isight USB camera on my macbook 3,1 to function properly. during this time, i have used isight-firmware-tools on two completely different installations of ubuntu 10.10, one in a partition and one replacing osx entirely, extracting the firmware both from the already existing firmware in the mac installation and from a downloaded file. most recently, i followed the instructions recommended by [this]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight") page, and problems are still cropping up. the isight firmware IS being recognised on startup. i no longer have the error message, etc. however, applications fail to recognise it's existence. cheese, which before started and then threw an "error, no camera recognised" message now stops responding immediately upon startup without having displayed anything. everything else, however, acts no differently with the firmware in place than it did before. i opened gstreamer-properties and it does not detect any video devices either. what now?

---

### Post by shmibs on 2011-04-12
*bump* i have gotten the camera to work successfully since my last post, but only if i login using KDE. when logging into the gnome environment initially it still does not function. however, logging in and out of KDE and subsequently logging into ubuntu desktop edition causes the isight camera to be recognised and functional. is there possibly something that should be running upon starting ubuntu desktop edition that is not? any help is appreciated. thanks!

---

