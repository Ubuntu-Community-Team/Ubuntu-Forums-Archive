---
title: "Lubuntu 13.04 Install on ASUS U32U-ES21"
date: 2013-06-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dizzpozable on 2013-06-07
Here are a few things that helped me get Lubuntu 13.04 running on my ASUS U32U-ES21 (which I love). Hopefully it can save someone some time.

[COLOR=#000000][FONT=Helvetica]- Fix wireless hardware lock[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]http://ubuntuforums.org/showthread.php?t=2142462&page=2[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Helvetica]# printf "\nblacklist asus_nb_wmi\n" >> /etc/modprobe.d/blacklist.conf && reboot[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Helvetica]- Fix sound[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]http://chakra-project.org/bbs/viewtopic.php?pid=50909[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Helvetica]$ nano ~/.asoundrc[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=Helvetica]pcm.!default {[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]  type hw[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]  card SB[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]}[/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica]ctl.!default {[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]  type hw[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]  card SB[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]}[/FONT][/COLOR]
```

Then log out and log back in.

[COLOR=#000000][FONT=Helvetica]- Install mainline kernel (not a fix, just a bonus)
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Helvetica]#!/bin/bash

[/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]# mainline.sh - checks for and installs latest ubuntu mainline kernel
# https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme

if [ $UID -ne '0' ]; then
        echo "Error: mainline.sh must run as root"
        exit
fi

cd /tmp

wget https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater/archive/master.zip -O Ubuntu-Mainline-Kernel-Updater.zip && \
unzip Ubuntu-Mainline-Kernel-Updater.zip

chmod +x Ubuntu-Mainline-Kernel-Updater-master/install
./Ubuntu-Mainline-Kernel-Updater-master/install

KernelUpdateChecker -no-rc

./kernel-update[/FONT][/COLOR]
```

---

