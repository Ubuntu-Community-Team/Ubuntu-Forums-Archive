---
title: "KDE in Edgy"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-10-26
Hi there,

It took me about a month to get Dapper setup and working perfectly with KDE. I want to update to the latest and the greatest so will my current KDE setup work with the Edgy upgrade. I'n not going to download the ISO and do a clean install, just do an upgrade. Will the latest version of KDE run on Edgy(has some one tried this) and then finally, is it possible to do an upgrade from the cd. with Dapper I had to do a clean install.

Thanks,

Rudolf

---

### Post by Marsolin on 2006-10-26
I haven't tried it yet, but it should be. You could also upgrade by editing your repositories (/etc/apt/sources.list) and replace dapper with edgy, then run the following commands.

sudo apt-get update
sudo apt-get dist-upgrade

Any modifications that you made to the original KDE settings should be saved in your home directory and those will not be overwritten by the upgrade.

---

### Post by RudolfMDLT on 2006-10-26
Thanks! 

One more question though, can I install Ubuntu and then update my KDE to the latest version as well?

---

### Post by Marsolin on 2006-10-26
If you are doing a CD only install then that should work. You can update KDE over the network later.

---

### Post by RudolfMDLT on 2006-10-26
Okay, but do you mean upgrade with a cd install or do you mean fromat and then cd install?

---

### Post by RudolfMDLT on 2006-10-26
No matter. Downloading the alternate install cd. It will allow me to update from the disc and if the crap hits the fan i can do a clean install from the disc!

---

