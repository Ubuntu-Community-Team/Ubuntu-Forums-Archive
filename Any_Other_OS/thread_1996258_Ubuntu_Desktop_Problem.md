---
title: "Ubuntu Desktop Problem"
date: 2012-06-04
forum: Any Other OS
---

### Post by cozski on 2012-06-04
I've installed Zorin OS 5.2 for 32bit system and during installation  ubuntu-desktop failed to install correctly. As Zorin is a Ubuntu based  OS I used the Update Manager to upgrade to latest LTS and thought this  might resolve the broken ubuntu-desktop package. However, this does not  appear to have worked. When I try sudo apt-get install --reinstall ubuntu-desktop I get this output: Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:  The following packages have unmet dependencies:  ubuntu-desktop : Depends: unity but it is not going to be installed E: Unable to correct problems, you have held broken packages.

 Not sure if this is related but Synpaptic Package  Manager tells me Ubuntu One is installed but I can't find the Folder  and there is no context menu option to sync other folders. Suggestions  welcomed.

---

### Post by lisati on 2012-06-04
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by drawkcab on 2012-06-04
Honestly, I would just install the newest version of Zorin from scratch.  I rarely trust the updater when its vanilla ubuntu, let alone the ubuntu updater of a distro branched from ubuntu.  I've found that while the updater tends to work just fine over all, you still wind up with a number of these little gremlins that plague you until you reinstall from scratch.

---

### Post by cozski on 2012-06-05
Thanks.... yeah the problem has popped up for others from my quick perusal of the web but none seem to provide a concise solution... I installed to my PC no problem so maybe a re-install is required  Cheers.

---

### Post by critin on 2012-06-05
> **cozski said:**
> Thanks.... yeah the problem has popped up for others from my quick perusal of the web but none seem to provide a concise solution... [COLOR=Red]I installed to my PC no problem[/COLOR] so maybe a re-install is required  Cheers.

> I've installed Zorin OS 5.2 for 32bit system and [COLOR=Red]during installation  ubuntu-desktop failed to install correctly.[/COLOR] These two statements appear to conflict with each other.  Probably a fresh install would be a good idea.

This link tells how to deal with broken packages.  I've found that updating forked versions doesn't always work smoothly because many things are changed to make the new version.  

[http://zoringroup.com/forum/viewtopic.php?f=6&t=1618](http://zoringroup.com/forum/viewtopic.php?f=6&t=1618)

This link might help too.  Warnings and advice.

[http://www.zoringroup.com/forum/viewtopic.php?f=6&t=2054](http://www.zoringroup.com/forum/viewtopic.php?f=6&t=2054)

---

### Post by cozski on 2012-07-02
There is no conflict as one version was installed on my PC and one on my laptop - maybe should have been clearer on that. Anyway, I fixed Broken Packages by booting into recovery mode and that seemed to resolve the problem... however several upgrades started causing havoc with the desktop so I've ditched it. Opting for Mandriva for a while, see how I get on... thanks for the reply and link by the way, appreciated.

---

