---
title: "sad problem?????????????"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-08-08
i have very sad problem with me.my proxy server is blocking files that have size greater than 3Mb ,but i can download these files in my xp with an anonymous proxy software.but when i download something and copy paste it into 
/var/cache/apt/archives and type apt-get ,it does not look in the hard drive 
rather it tries to download from the internet,which is blocked by proxy server.so i can't install them
i also tried synaptic but same thing happend
how to force apt-get and synaptic to first search from the hard drivr and then from internet.

 how can i burn thes debs on cds and make my cd rom as repository?

---

### Post by hotbrainz on 2006-08-08
you can using these steps:

Download the packages you want.
Burn them on a cd.
Pop it into your Ubuntu box.
Go to System > Administration > Synaptic Package Manager
Go to Edit > Add CD-ROM
Add it as a source.
Go to Settings > Repositories
Uncheck every box except the one you just added
Click Reload
Search for whichever package you want to install from your cd
Mark it for installation.
Apply Changes.

Courtesy : Aysiu


This I did when i was new to Ubuntu

Hope this helps.

Cheers

---

