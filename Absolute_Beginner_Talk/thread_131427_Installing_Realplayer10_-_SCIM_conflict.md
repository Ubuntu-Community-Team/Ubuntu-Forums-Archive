---
title: "Installing Realplayer10 - SCIM conflict?"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by JungleBeast on 2006-02-16
Hello all!   I'm trying to install Realplayer10 on Breezy, as it's the only way to listen to bbc. I'm following the FAQs and i've done the download a couple times, only to find that Firefox no longer works. So I just started again, reinstalling Breezy..   So rather than going through the whole install every time I get it wrong to be able to get back online to find more info, I'd like to get it right first time (this time!)
So far I've got:

cd ~/Desktop
sudo apt-get install libstdc++5
chmod +x RealPlayer10Gold.bin
sudo ./RealPlayer10Gold.bin

and it all seems to install fine  -  I got this from the Ubuntu wiki
the icon appears in applications and everything, but Realplayer does not launch and Firefox no longer launches.

So (also in ubuntu wiki) I found that RealPlayer and Breezy sometimes have SCIM conflicts and that to fix this to:

sudo gedit /usr/bin/realplay

and then to edit the line after the bash declaration statement:


#!/bin/sh

GTK_IM_MODULE=xim ; export GTK_IM_MODULE


I followed all this, but it still hasn't resolved the problem.

So has anyone got any ideas? I'm just trying to install realplayer on a fresh breezy install on an amd64, surely everyone else doing this should have the same conflict? :confused: 
well thanks for any help! :-D

---

### Post by JungleBeast on 2006-02-17
The wiki address is here:   [https://wiki.ubuntu.com/RealplayerInstallationMethods]("https://wiki.ubuntu.com/RealplayerInstallationMethods")

Any ideas? Have I typed something wrong? :confused:

---

