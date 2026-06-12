---
title: "Ubuntu on my Macbook"
date: 2007-05-21
forum: Apple Intel Users
---

### Post by erakepio on 2007-05-21
Hey Guys,

Been using Ubuntu for a while on my PC (Had some ATi issues to work around!) and decided to put it on my macbook.  Installed and it's up and running ALMOST perfectly dual booting alongside MAC OS (no bootcamp!).  Few issues I have are minor ones...

1) Right Click - How do i enable this for my macbook?  in MAC OS ive always tapped the trackpad with 2 fingers or held down CTRL but this has no effect in Linux

2) Trackpad appears a little sluggish on Ubuntu..and at times is un responsive and very un-sensitive

3) Screen resolution only goes p to 1024x768...obviously i'm trying to get widescreen resolution (like on MAC OS)

Any ideas on these issues and how they might/may be resolved.

Cheers

---

### Post by ronocdh on 2007-05-21
> **erakepio said:**
> Hey Guys,

Been using Ubuntu for a while on my PC (Had some ATi issues to work around!) and decided to put it on my macbook.  Installed and it's up and running ALMOST perfectly dual booting alongside MAC OS (no bootcamp!).  Few issues I have are minor ones...

1) Right Click - How do i enable this for my macbook?  in MAC OS ive always tapped the trackpad with 2 fingers or held down CTRL but this has no effect in Linux

2) Trackpad appears a little sluggish on Ubuntu..and at times is un responsive and very un-sensitive

3) Screen resolution only goes p to 1024x768...obviously i'm trying to get widescreen resolution (like on MAC OS)

Any ideas on these issues and how they might/may be resolved.

Cheers
Try installing Gsynaptics or Qsynaptics via the terminal. This will give you better options to mess with trackpad speed and even set up tapping. In the meantime, know that F11 and F12 are middle and right click by default, that's what I use. Some people remap and use the right Cmd key and the Enter key beside it, but I'm happy with F11 and F12 for the time being.

You'll have to add **"SHMConfig"** and set it to **"true"** in your xorg.conf. Trying to run G/Qsynaptics without doing this will throw an error, asking you to do it.

Please post more info about your hardware. If you have a MacBook Pro, the Restricted Drivers Manager should provide you with the fgrlx driver. If not, you can do ```
sudo apt-get install xorg-driver-fglrx
```With a MacBook, you'll have Intel integrated graphics, so instead you'll want to type ```
sudo apt-get install 915resolution
```Once that's done with either one: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Good luck!

---

### Post by erakepio on 2007-05-21
Thanks for your reply ronocdh.  It's just a standard Macbook

good news and bad news! firstly, i managed to solve the screen resoluion issue with relative ease.

onto the right click..F12 and F11 doesnt seem to work for me (my keyboard settings are set to UK: Macintosh.

i tried running a script which i found on these forums which attempts to solve the problem..however i couldnt get it to run (probably just me!)

Trackpad I managed to fix also (again thx for help).


However, I'm now unable to get any Wireless Connectivity going.  I've ndiswrapper without success.  I'm about to try MadWifi but at the moment thats all i can thing of.  I tried "sudo iwlist ath0 scan" but i got "This device does not have a scanning interface"

any tricks?

---

### Post by ronocdh on 2007-05-21
> **erakepio said:**
> However, I'm now unable to get any Wireless Connectivity going.  I've ndiswrapper without success.  I'm about to try MadWifi but at the moment thats all i can thing of.  I tried "sudo iwlist ath0 scan" but i got "This device does not have a scanning interface"

any tricks?
Does your MacBook have a Core Duo or a Core2 Duo processor? This matters. Also, please type:```
sudo update-pciids
```Then:```
lspci
```And give us the info on your wireless chipset. (It will be near the bottom of the list.) That will be helpful for offering solutions.

The wireless connection you're trying to connect to, is it encrypted? With what (WEP, WPA, WPA2)?

---

### Post by erakepio on 2007-05-21
I believe it is Core 2 Duo.  Here is the info on my wireless card..

02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

The network i will be connecting will have WPA Security.  At the moment I've only set the router for my net connection etc.  Been trying for a few hours to get this wireless to work on macbook for ubuntu

---

### Post by ronocdh on 2007-05-21
> **erakepio said:**
> I believe it is Core 2 Duo.  Here is the info on my wireless card..

02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

The network i will be connecting will have WPA Security.  At the moment I've only set the router for my net connection etc.  Been trying for a few hours to get this wireless to work on macbook for ubuntu
I would try downgrading your network's encryption to WEP and testing with that. 
Have you seen [widemos's post]("http://ubuntuforums.org/showthread.php?t=429641&highlight=widemos+ndiswrapper") on configuring MadWifi? BSantos posted a redaction later in the thread that I think helped a few out beyond what widemos's did. 

Good luck, post back with results!

---

### Post by ramcosca on 2007-05-23
> **erakepio said:**
> I believe it is Core 2 Duo.  Here is the info on my wireless card..

02:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

The network i will be connecting will have WPA Security.  At the moment I've only set the router for my net connection etc.  Been trying for a few hours to get this wireless to work on macbook for ubuntuI don't have much to provide, but I can say that it is a C2D. Only C2Ds come with WiFi-n.

---

### Post by ivesjd on 2007-05-23
Does anyone know the keycode for F12 on the macbooks? xev doesnt work as the F12 key is set to right click.

---

### Post by ramcosca on 2007-05-23
I just installed Feisty Fawn on my MacBook using Fusion. I tried doing what was previously mentioned: ```
sudo apt-get install 915resolution
```... but it did not work. It says: ```
Wrong chipset detected. 915resolution only works with Intel 800/900 series graphic chipsets.
```MacBooks have an Intel GMA950 integrated graphics card... What am I doing wrong?

---

### Post by ivesjd on 2007-05-23
Are you using vmware fusion or a pure install?

---

### Post by techdude2007 on 2007-05-24
With trying to right click with a Mac in Linux, try clicking Apple Key (the the apple logo) and then clicking the mouse.

---

### Post by DoctorGonzo on 2007-07-14
> **techdude2007 said:**
> With trying to right click with a Mac in Linux, try clicking Apple Key (the the apple logo) and then clicking the mouse.

thanx amigo- works out fine with the right apple key... no need to edit anything!:):)

---

