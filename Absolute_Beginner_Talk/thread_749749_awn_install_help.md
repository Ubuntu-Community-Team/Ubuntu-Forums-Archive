---
title: "awn install help"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by mstrchfmjolnirty on 2008-04-08
alright so im attempting to install mac4lin and ive got it  all fantastic right now...icons window look, login screen...all that but im  working on the dock and i cant get AWN to install properly i try using this guide:

[http://ubuntuforums.org/showthread.php?t=572019&highlight=HOWTO+awn](http://ubuntuforums.org/showthread.php?t=572019&highlight=HOWTO+awn)

and i get to the end and when i open it from applications nothing happens same when i try awn settings from system>preferences...i tried again and now the icons arent even there...so basically i would appreciate like a way to completely get rid of what ive done so far and restart....including  the compository sources and everything...any help with this would be fantastic...i am kind of a noob as i just installed ubuntu on my laptop last night...thanks again

---

### Post by fenian on 2008-04-08
First get rid of everything,open a terminal and type (enter each line seperately)...

> sudo rm -f /usr/local/bin/awn*
sudo rm -f /usr/local/bin/avant*
sudo rm -rf /usr/local/lib/awn
sudo rm -f /usr/local/share/locale/*/LC_MESSAGES/avant-window-navigator.mo
sudo rm -f /usr/local/share/applications/avant*
sudo rm -f /usr/local/share/applications/awn*
sudo rm -rf /usr/local/share/avant-window-navigator
sudo rm -f /usr/local/lib/libawn*
sudo rm -rf /usr/local/include/libawn
sudo rm -f /usr/local/lib/libawn*
sudo rm -f /usr/local/lib/pkgconfig/awn.pc
sudo rm -rf /usr/local/share/awn-core-applets
sudo rm -rf /usr/local/lib/python2.5/site-packages/awn/

Next install AWN for Gutsy open a terminal and type (enter each line seperately)...


> echo 'deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'  |  sudo tee -a /etc/apt/sources.list
echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'  |  sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

Start AWN from Applications->Accessories->Avant Window Navigator.

---

