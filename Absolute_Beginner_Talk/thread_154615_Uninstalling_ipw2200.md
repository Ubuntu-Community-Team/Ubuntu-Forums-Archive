---
title: "Uninstalling ipw2200"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by Goonie on 2006-04-03
Hello all

I've given up on trying to get wireless to work on Breezy and since the wireless worked "out of the box" in Warty using ndiswrapper instead of ipw2200, I thougt I'd try to switch drivers. Can anyone help me with the uninstallation of ipw2200 or point me to a good how-to?

Thx
Goonie

---

### Post by YuHoo on 2006-04-03
ok, I've had tons of problems with breezy and ipw2200 as well. The out of box working is through manually configuring the wireless in the install, and that has an outdated driver (1.0.6). So I'll walk you through both the uninstall and install (if you want to give it another shot)

To uninstall you need to simply "make uninstall" while in the ipw2200 folder. That simple.

To install, get the newest ieee80211b drivers, if you haven't done so already, at [http://ieee80211.sourceforge.net/index.php]("http://ieee80211.sourceforge.net/index.php"). The biggest thing you need to do is not to follow their instructions. 

Untar it with and then enter its folder to make and make install
```
tar -xzvf ieee80211-1.1.13.tgz
make
make install
```
If you have any errors check below the download area where they have a fix for it.

Then get the stable releases of ipw2200, the newest versions do not work all the time. [http://ipw2200.sourceforge.net/]("http://ipw2200.sourceforge.net/"). Make sure to get the ipw2200-1.1.0.tgz and the firmware v2.4

```
tar -xzvf ipw2200-fw-2.4.tgz
sudo cp ipw2200-fw-2.4 /lib/hotplug/firmware
```
Now your firmware is installed, all you need is the drivers.

```
tar -xzvf ipw2200-1.1.0.tgz
cd ipw2200-1.1.0
sudo make
sudo make install
```
I had to sudo it, I don't know why, but I did, so I hope it works for you. With that you should have your ipw2200 working. If not, I'm sorry but good luck with Warty.

---

### Post by Goonie on 2006-04-04
[QUOTE=YuHoo]

To uninstall you need to simply "make uninstall" while in the ipw2200 folder. That simple.

[/QUOTE]

I'm not sure I understand you here? from which folder is that exactly? The only ipw2200 folder I find is /lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ipw2200  

If I do "make uninstall" from there I get "make: *** No rule to make target `uninstall'.  Stop."

The only file in this directory seemst to be ipw2200.ko , nothing else.

Sorry if my questions are silly, I'm really a newbie in linux.

Thx
Goonie

---

### Post by YuHoo on 2006-04-05
It's a good question, I was assuming that you compiled your own drivers before. Since you didn't, the drivers that you have installed are probably 1.0.6 standard install from Breezy and don't worry about those. When you unpack and make the ipw2200 drivers (the new ones) the make program will run a check and will remove old drivers like the .ko. I just always run the program uninstall then allow the new one to take over any loose ends.

I hope this solves your problems, the ipw2200 seems to be finicky in Breezy, but they could solve that by putting ieee and ipw in dapper.

---

### Post by Goonie on 2006-04-09
Thanks for all your help guys.

No matter what I tried, nothing seemed to work. I then tried to exchange the mini-pci card and reinstall Breezy and voilá... wireless worked =o

So I'm not messing with this for now, gonna use the 1.0.6 driver until I move up to Dapper when it's stable. 

Goonie,
Online and happy

---

