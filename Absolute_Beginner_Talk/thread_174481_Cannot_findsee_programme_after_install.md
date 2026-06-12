---
title: "Cannot find/see programme after install ??????"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by weiyang on 2006-05-11
It is my 3rd day fiddling with ubuntu.... and it's driving the missus nuts " windows just ponit and click".....

1. Anyway, I have install ClamAV via synaptic BUT cannot see the prog in any icon. So is it running??? How to configure it if I can't find it......

2. Firestarter, is install and running but notice that the blue "play" icon on the menu bar turns red after awhile. What does this means?

Help, Thanks.:confused:

---

### Post by enopepsoo on 2006-05-11
You can go into synaptic and find the package, then go to properties.  You can view the installed files from there.  The exectuable will be something in /usr/bin or /usr/share/bin.
Since it is an antivirus, you should probably check in services under system > administration.
Also try typing ```
man clam
``` or variations like clamav etc at the prompt to see the manual for the clamAV.
Usually man is very helpful.

---

### Post by Qrk on 2006-05-12
Sadly, not all programs in the repositories available through Synaptic are set up to give an icon in Ubuntu's menu. A good work around is to install the Debian menu, (its the package "menu" in Synaptic) which lists more applications. You'll have to add it through the menu editor. 

Once you know the command for a package you installed through Synaptic, you'll have to add it to your menus manually.

---

### Post by Clay85 on 2006-05-12
[QUOTE=Qrk]Sadly, not all programs in the repositories available through Synaptic are set up to give an icon in Ubuntu's menu. A good work around is to install the Debian menu, (its the package "menu" in Synaptic) which lists more applications. You'll have to add it through the menu editor. 

Once you know the command for a package you installed through Synaptic, you'll have to add it to your menus manually.[/QUOTE]


I have that debian menu installed, but it's greyed out in the menu editor. Why can't I use it?

---

### Post by confused57 on 2006-05-12
I don't know if there is a GUI way of running ClamAV(don't think so):

[https://wiki.ubuntu.com/ClamAV](https://wiki.ubuntu.com/ClamAV)

---

### Post by weiyang on 2006-05-12
Still can't "see" ClamAV but is definitely running in the background as found it in services and during shutdown notice a promt that ClamAV was being stopped prior to complete shutdown. Well I think I will leave it at that for the time being..... Thanks all for replying.:)

---

### Post by nalmeth on 2006-05-12
You may prefer [this anti-virus program]("http://www.ubuntuforums.org/showthread.php?t=136064")

---

