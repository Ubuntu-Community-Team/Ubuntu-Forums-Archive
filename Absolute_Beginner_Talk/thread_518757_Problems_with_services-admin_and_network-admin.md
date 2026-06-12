---
title: "Problems with services-admin and network-admin"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by mewt on 2007-08-06
Hi,

I have suddenly realised that i am unable to run neither services-admin or network-admin from the menu...All i get is the window but no contents and looks like it has crashed. I am unable to close the window and thus have to resort to killing it. I tried it as soon as i logged into the session and network-admin worked for a few seconds, Then hanged. The only difference i noticed on the system was the spawning of 4 perl processes:

root      4702  0.0  0.1   2872   816 ?        Ss   14:57   0:00 /usr/bin/system-tools-backends
root      6086  0.2  1.6  14224 12448 ?        S    15:05   0:00 perl /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m HostsConfig
root      6090  0.2  1.5  13696 11776 ?        S    15:05   0:00 perl /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m Platform
root      6096  0.2  1.8  16224 14472 ?        S    15:05   0:00 perl /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m IfacesConfig
root      6233  1.4  1.6  14636 12892 ?        S    15:07   0:00 perl /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m ServicesConfig
root      6262  0.0  0.0   2884   752 pts/0    R+   15:07   0:00 grep system-tools-backend

What can I do to fix this, it is extremely important for me as this is  work laptop and I would need to change system settings several times. 

Thanks

Mewt

---

### Post by Damanther on 2007-08-06
Which version are you running and which desktop??

If you are running the kde desktop, the gnome admin utils don't always work real well even though they still show up in your Kmenu.

---

### Post by mewt on 2007-08-07
im running feisty fawn, with gnome but with the base kde libraries installed so as to be able to run k3b. 

THe strange thing is that as soon as i boot up and log in i can go into the network-admin window and i can see the interfaces etc but after a few seconds the applet crashes. When i try to run it again, I get the above mentioned empty window

---

### Post by Damanther on 2007-08-07
Try using KNetwork manager, under KMenu->Internet.

Or alternatively, run kcontrol which has a network settings option.

---

