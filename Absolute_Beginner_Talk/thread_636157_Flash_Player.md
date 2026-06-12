---
title: "Flash Player"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by handsoffate on 2007-12-09
I know helpful people here deal lots of questions regarding flash player insttallation but after trying hundreds of methods and not coping with it  I decided to post here. I can't install flash player... Last method I tried was by using the terminal and all I get is this: 

21:05:44 (15.38 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Can someone help me to solve this issue please?

---

### Post by Johnny3 on 2007-12-09
try Mr daradib  idea just about bottom of page.   [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=634756](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=634756)
You can down load it and use GDebi Package installer.  Application/system tools  if GDebi isn't there Right click on Applications and Edit menus to add it. Ubuntu has a lot of stuff hided.
Hope it works. It did for me.
Thanks Johnny3
Gainesville fl

---

### Post by overdrank on 2007-12-09
> **handsoffate said:**
> I know helpful people here deal lots of questions regarding flash player insttallation but after trying hundreds of methods and not coping with it  I decided to post here. I can't install flash player... Last method I tried was by using the terminal and all I get is this: 

21:05:44 (15.38 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Can someone help me to solve this issue please?

HI and welcome, maybe this link can help
[https://help.ubuntu.com/community/FlashPlayerStandalone](https://help.ubuntu.com/community/FlashPlayerStandalone)

---

### Post by FuturePilot on 2007-12-09
Because Adobe released a new version of Flash, there's an MD5sum mismatch in the flashplugin-nonfree package. You'll have to install manually for right now.
First remove the flashplugin-nonfree package
```
sudo apt-get remove --purge flashplugin-nonfree
```
Then go [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") and download the .tar.gz package to your Desktop. Right click on it and "Extract Here"
Then open a terminal and 
```
cd Desktop/install_flash_player_9_linux/
```
Then run the installer script
```
sudo ./flashplayer-installer
```
Follow the directions and when it asks you for a path to the browser enter
```
/usr/lib/firefox
```

---

### Post by handsoffate on 2007-12-09
Thank you very much for your help FuturePilot. I solved the problem thanks to your suggestion...

---

### Post by blk97tt on 2007-12-09
FuturePilot's instructions worked for me as well.  Thanks :)

---

### Post by meborc on 2007-12-09
this fix does not work with opera (using /usr/lib/opera in installer)

no flash can be seen anymore... the firefox fix works, but it is slow as hell on my 256M ram lappy :S

---

### Post by FuturePilot on 2007-12-09
> **meborc said:**
> this fix does not work with opera (using /usr/lib/opera in installer)

no flash can be seen anymore... the firefox fix works, but it is slow as hell on my 256M ram lappy :S

The latest version of Flash is broken in Opera and Konqueror or any non GTK browser for that matter :(

---

### Post by MavrikX4 on 2007-12-09
I am running an AMD 64 processor and the above fix didn't work for me.  Any suggestions?

---

### Post by CDL-WarChilde on 2007-12-10
Ubuntu 7.10+compiz enabled and Opera 9.24 = no flashy (home PC)  video card is X300 PCI-e.

Ubuntu 7.10 without compiz and Opera 9.24 = flash work (PC at work)  video card is AIW 7000 AGP.

7.04 flash worked fine on both machines with Opera 9.24 and flash.

---

### Post by daradib on 2007-12-10
See this for more information: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by Gonkers on 2007-12-19
> **FuturePilot said:**
> The latest version of Flash is broken in Opera and Konqueror or any non GTK browser for that matter :(

Could you please elaborate? I have "successfully" installed the latest version of the flash plugin. It works fine in firefox, but I just get blank boxes in Opera with a tool tip of "Title: Click to activate and use this control."  I have checked the plugins section of Opera and it appears to be installed/recognized but just doesn't work.

application/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/opera/plugins/libflashplayer.so

---

### Post by designzinthesun on 2007-12-22
> **FuturePilot said:**
> Because Adobe released a new version of Flash, there's an MD5sum mismatch in the flashplugin-nonfree package. You'll have to install manually for right now.
First remove the flashplugin-nonfree package
```
sudo apt-get remove --purge flashplugin-nonfree
```
Then go [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") and download the .tar.gz package to your Desktop. Right click on it and "Extract Here"
Then open a terminal and 
```
cd Desktop/install_flash_player_9_linux/
```
Then run the installer script
```
sudo ./flashplayer-installer
```
Follow the directions and when it asks you for a path to the browser enter
```
/usr/lib/firefox
```

This works every time. I've reloaded Ubuntu 7.10 a few times after trying other distros. Ubuntu works the best with my old mix and match system and it's also the easiest for me (new to linux) to work with. Thank you everyone of Ubuntu and thank you Jesus.

---

