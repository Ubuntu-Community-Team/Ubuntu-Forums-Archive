---
title: "Automatic Updates Issue"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by xcesarfrancox on 2007-08-27
Hi there you guys

I'm very new at Linux world, but I've managed to get my desktop very nice and sweet and every thing is going out smoothly, but...

One day I noticed that GNOME wasn't warning me about updates, I have had an orange star on my upper panel that indicates me that updates were available, but suddenly that star wasn't appearing anymore, so I went to System > Administration > Software Sources, at the updates tab, the check box "Check for updates" under Automatic Updates was unchecked, so I checked it to have my Ubuntu to warn me about updates again, but when I close Software sources window I re-open it again but the check box is again unchecked... I managed to update through console with a simple:

sudo aptitude update

sudo aptitude upgrade

but I don't have the automatic check for updates, and I have to do that manually, and I would like my PC to check for updates every day and download them automatically... so any help would be so so so much appreciated... thanks for reading me, see ya!

:)

---

### Post by cawill on 2007-08-27
Under sessions (in preferences)in the startup programs tab is update-notifier still there?, also run 'update-notifier' to install the updates using GUI.

---

### Post by xcesarfrancox on 2007-08-27
Yup, the Update notifier is still there, and even I tried to run update-notifier but it seems I can't get enabled the "Check for updates" thing... :(

---

