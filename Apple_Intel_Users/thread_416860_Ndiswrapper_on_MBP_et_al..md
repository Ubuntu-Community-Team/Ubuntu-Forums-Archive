---
title: "Ndiswrapper on MBP? et al."
date: 2007-04-21
forum: Apple Intel Users
---

### Post by ronocdh on 2007-04-21
Hey guys, I haven't gotten wireless up on Feisty yet. When following the classic [MacBook guide]("https://help.ubuntu.com/community/MacBook"), I get this error at the **echo** stage:
```
~$ sudo echo >> /etc/modules "ndiswrapper"
bash: /etc/modules: Permission denied

```
Don't really know how to deal with this. I saw a nice post by yannoo that says:
> OK, tested succesfully the AR5418 on my MacBook Pro with Feisty Fawn by using ndiswrapper:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndiswrapper-source
cd
mkdir drivers
cd drivers
wget <IBM-DriverFor5416-AsMentionedInThisThread>
tar zxvf <IBMDriver.tar.gz>
sudo ndiswrapper -i NET5416.INF
sudo vi /etc/modules <edit to add "ndiswrapper">
sudo modprobe ndiswrapper
sudo iwconfig
```

After this, I might have restarted X, not sure.
Problem is, I can't find mention of this IBM drive in the (20-page!) thread. =( I think I can just substitute the Apple XP one, but I'm not quite sure.

Also, my screen brightness keys don't work; they bring up a little GUI box, but no indicator as to how bright the screen is currently or is becoming. Last, my volume keys adjust only my headphone volume, which is very annoying when I'm using speakers. =) Anyone know how to fix?

Thanks!

---

### Post by Tyrdium on 2007-04-21
Haven't tried the wireless yet, having the same issue with brightness control. I did get the sound control working, though. System -> Preferences -> Sound, go to Default Mixer Tracks, HDA Intel (Alsa mixer) in the dropdown, make sure Headphone and Speaker are selected. That'll make it so your volume keys work as a master volume control.

---

### Post by ronocdh on 2007-04-21
> **Tyrdium said:**
> Haven't tried the wireless yet, having the same issue with brightness control. I did get the sound control working, though. System -> Preferences -> Sound, go to Default Mixer Tracks, HDA Intel (Alsa mixer) in the dropdown, make sure Headphone and Speaker are selected. That'll make it so your volume keys work as a master volume control.
Sound tip worked like a charm, thank you. I heard brightness worked OOB in Feisty, so I don't want to install some other software package to do it. At least then I could type "backlight +10" in the console or something, even assign in a keybind, but I don't want (yet more!) nasty conflicts.

---

### Post by Tyrdium on 2007-04-21
Oho! Got the keyboard controls working.

sudo aptitude install pommed, edit /etc/pommed.conf to your liking (defaults are good, but I changed fnmode to 2 so the F# keys works as F# keys (that is, fn+F# for backlight/volume/whatever)). Do a 'sudo /etc/init.d/pommed restart' after making changes to the config file.

---

### Post by ronocdh on 2007-04-21
> **Tyrdium said:**
> Oho! Got the keyboard controls working.

sudo aptitude install pommed, edit /etc/pommed.conf to your liking (defaults are good, but I changed fnmode to 2 so the F# keys works as F# keys (that is, fn+F# for backlight/volume/whatever)). Do a 'sudo /etc/init.d/pommed restart' after making changes to the config file.
Niiiice, thank you. Let me know whether you get wireless working! I might bite down and try [this]("http://ubuntuforums.org/showthread.php?t=415543") tonight. :twisted:

---

### Post by Tyrdium on 2007-04-21
Wireless via NdisWrapper, you mean? I tried installing the AR5416 driver located [here](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-66449), but for some reason it isn't seeing the device. The driver installs just fine, but the card isn't showing up. Which is odd, because I can see it through lspci.

---

### Post by ronocdh on 2007-04-21
> **Tyrdium said:**
> Wireless via NdisWrapper, you mean? I tried installing the AR5416 driver located [here](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=MIGR-66449), but for some reason it isn't seeing the device. The driver installs just fine, but the card isn't showing up. Which is odd, because I can see it through lspci.
Well I don't like the sound of that one bit. I can try that driver on my hardware--not that it's all that different ;)--and then I can also grab the Apple driver for XP, because I still have XP on a party on here.

We shall see.

---

