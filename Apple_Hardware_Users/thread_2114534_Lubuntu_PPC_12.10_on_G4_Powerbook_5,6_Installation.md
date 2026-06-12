---
title: "Lubuntu PPC 12.10 on G4 Powerbook 5,6 Installation"
date: 2013-02-10
forum: Apple Hardware Users
---

### Post by padre999 on 2013-02-10
Hello

I just installed Lubuntu 12.10 on a G4 1,67 Ghz Powerbook 5,6, and wanted to share my experiences, for anybody who might try the same.

First problem I ran into after booting from the PPC LiveCD was that I could not run the installer since there is only an empty window displayed. The problem is that Lubuntu boots into 8bit color mode on this machine. To fix that you have to boot the cd using

```
live video=radeonfb:1280x854-32@60
```

Wifi is not working, that will be fixed after the installation. To have internet I used an ethernet cable connection.

Once installed and inside the new system I ran

```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```

to fix the Wifi. After a reboot it worked.

Next problem was sound. I had to alter the file etc/modprobe.d/blacklist.local.conf to

```
# Local module settings
# Created by the Debian installer

# blacklist snd-aoa-codec-tas
# blacklist snd-aoa-fabric-layout
# blacklist snd-aoa-i2sbus
# blacklist snd-aoa-soundbus
# blacklist snd-aoa

```

and the file etc/modules to

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

# snd_powermac
# apm_emu
# loop
# snd-powermac
# therm_adt746x
snd-aoa-codec-tas
snd-aoa-fabric-layout
snd-aoa-i2sbus
snd-aoa-soundbus
snd-aoa

```

After a reboot I ran "alsamixer" in a Terminal and had to bring up the PCM Volume which was down to 0. Now I have sound too. Microphone is not working though, no idea why.

Flash videos (some of them) I got running using the Firefox Plugin Greasemonkey and this script:

[http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)

I installed the VLC browser plugin and disabled the other video and flash (gnash) plugins. Flash video is very jerky and without sound though. Still looking for a better solution.

Otherwise Lubuntu is running rather smooth, especially when compared to Ubuntu which I tried on this machine too.

---

### Post by danield on 2013-02-11
> Flash videos (some of them) I got running using the Firefox Plugin Greasemonkey and this script:

[http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)

I installed the VLC browser plugin and disabled the other video and flash (gnash) plugins. Flash video is very jerky and without sound though. Still looking for a better solution.

I use this userscript to display the download links:

[http://userscripts.org/scripts/show/87659](http://userscripts.org/scripts/show/87659)

and then use the "Open With" add-on to create a new menu entry that allows you to open the links with right-click to an external player.  I use /usr/bin/mplayer with the arguments "-framedrop -cache 8192 -cache-min 10" and it works great.

---

### Post by padre999 on 2013-02-11
> **danield said:**
> I use this userscript to display the download links:

[http://userscripts.org/scripts/show/87659](http://userscripts.org/scripts/show/87659)

and then use the "Open With" add-on to create a new menu entry that allows you to open the links with right-click to an external player.  I use /usr/bin/mplayer with the arguments "-framedrop -cache 8192 -cache-min 10" and it works great.

Thank you, I will try that!

---

