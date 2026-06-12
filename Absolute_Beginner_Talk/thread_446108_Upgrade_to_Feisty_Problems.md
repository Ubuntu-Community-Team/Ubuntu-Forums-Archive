---
title: "Upgrade to Feisty Problems"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by deuchar1 on 2007-05-16
Hi guys,

I'm having problems upgrading my Edgy system to Feisty.
I used the upgrade option in the software updates - it downloaded all the stuff and started running ok but half-way through I get the error:

Could not install '/var/cache/apt/archives/nvidia-glx-dev_1%3a1.0.9631+2.6.20.5-15.20_i386.deb
subprocess pre-installation script returned error exit status 2

Does anybody know why this is happening? It prevented the full upgrade and when I ran the partial upgrade fallback option I got the same error.

Thanks in advance,
Graham



Extra: 

Now I got....

Could not install the upgrades

The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed

---

### Post by Happy_Man on 2007-05-16
Yes... there have been many, many issues regarding these sub-process error scripts. I got 15 when I tried to install. Lucky you, you only got one. Unfortunately, the only way (so far as I know) to resolve is to completely do a fresh install. Hoping you have a /home partition.... [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome) is a howto on how to do that from an existing no /home install.... sorry. :(

---

