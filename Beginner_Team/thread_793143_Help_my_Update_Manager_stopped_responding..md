---
title: "Help my Update Manager stopped responding."
date: 2008-05-13
forum: Beginner Team
---

### Post by Mac_09 on 2008-05-13
Please tell me how to get it to either exit or start working again.  When I logged in today I had to install 35 updates, now it asked me to install another 7 and when I clicked install it froze up, it hasn't responded for almost an hour.

---

### Post by Living2007 on 2008-05-13
Either there is something wrong with your connection, or it has picked up a virus.

I wouldn't really know, I can't even get connected.

---

### Post by Bubba64 on 2008-05-13
> **Mac_09 said:**
> Please tell me how to get it to either exit or start working again.  When I logged in today I had to install 35 updates, now it asked me to install another 7 and when I clicked install it froze up, it hasn't responded for almost an hour.


There seems to be some problems with the update manager and general freezing of the overall Hardy distribution. When my update manager acts like its starting to update but nothing happens I do a force quit with the add on to the main panel. I then either go to synaptic where any listed updates are shown and install, you can also hit reload before or after the download to see if there are any more updates. You can also open the terminal and type sudo apt-get update then in put the password then let it load and type sudo apt-get upgrade to install. The previous post of a possible virus is incorrect. You can also add on to the panel system monitor so that you can see in real time what is going on.

---

### Post by Mac_09 on 2008-05-14
Thanks Bubba64, that's very helpful.  I sure hope they fix the problems with my distro soon :)

---

