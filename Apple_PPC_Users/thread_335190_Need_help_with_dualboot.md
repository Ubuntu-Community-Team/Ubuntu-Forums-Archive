---
title: "Need help with dualboot"
date: 2007-01-09
forum: Apple PPC Users
---

### Post by kevin_williams on 2007-01-09
Hi,
I have my iBook installed with Mac OS X and ubuntu.
Before, my computer would always prompt me which OS I wanted to run.

However, I noticed recently that my computer would startup and go straight to Mac OS X without prompting me.

Does anyone know how I could get my computer to prompt again?
TIA

---

### Post by kidders on 2007-01-10
Hi there,

Many OSX updates seem to overwrite bootloaders ... QuickTime upgrades, system security updates, etc. Perhaps this is what happened. The easiest way to reinstall your bootloader (yaboot, I presume) is to boot into any Linux envrironment with a boot CD and go from there.

---

### Post by handylinux on 2007-01-10
> **kevin_williams said:**
> Hi,
I have my iBook installed with Mac OS X and ubuntu.
Before, my computer would always prompt me which OS I wanted to run.

However, I noticed recently that my computer would startup and go straight to Mac OS X without prompting me.

Does anyone know how I could get my computer to prompt again?
TIA

I'm new at this, but from my experience (installed Ubuntu with OS X on a couple of iBooks) it sounds like: 

(a) In your installation of OS X, you never actually set the OS X partition as startup in the Startup Disk preference pane. As I recall, this setting is not done automatically during OS X installation, as it is generally unnecessary. So there was no setting in the computer's PRAM regarding what volume to startup from.

(b) Then you installed Ubuntu, probably on the first partition (as that is what is suggested in the instructions I've seen); and since no volume was specified in PRAM, the computer would startup from the first partition, which would give you the yaboot menu, from which you could select either Linux (by pressing **L**) or OS X (by pressing **X**).

(c) But then somehow the OS X partition/volume *was* set in Startup Disk. Perhaps you used Startup Disk to start from a different disk or CD, then used it again to switch back to OS X; or perhaps, as suggested by kidders, something you installed made this setting. In any case, once Startup Disk has been used, a setting has been recorded in PRAM, and there is no way to change that to a "null" setting in Startup Disk. And you cannot set your Linux volume in Startup Disk because it doesn't recognize it as a bootable System.

Or, possibly (d) you went through some command-line routines in Ubuntu to configure the computer so yaboot would load first (which I've read about but haven't tried, because I find such unnecessary; see below). But I believe that such a setting will be overridden simply by selecting your OS X partition in Startup Disk -- as in (c) above.

In any case, one thing you can try is to "zap the PRAM" by pressing command-option-P-R during startup; this should force the computer to repeat the startup process (you'll hear the startup chime repeated). Let it repeat the startup chime three times before unpressing the keys, whereupon it should startup from the first partition (the default if there is no Startup Disk setting in PRAM), and if you have Ubuntu on the first partition, you'll again see the yaboot menu.

However, there is an easier method to switch between OS X and Ubuntu: If Ubuntu is installed on the first partition, simply press the **D** key during startup, which forces the computer to start from the first partition, regardless of the setting in OS X's Startup Disk. If you use this method, and set OS X in Startup Disk, then when you start the computer without the D key, it will start in OS X, while with the D key it will start in Ubuntu. The yaboot menu will always appear when you start in Ubuntu, but if you simply do nothing, it will continue to startup Ubuntu; and you won't need to use it to "select" OS X.

From the information you've provided, it does sound like you have Ubuntu installed on the first partition, while OS X has been set in Startup Disk; if so, there is no need to go through anything to return to your previous situation, where what you were doing was slightly more complicated than the method I've described. Simply press **D** to start in Ubuntu, press nothing to start in OS X.

For more discussion of this, see [my post here]("http://www.ubuntuforums.org/showthread.php?p=1951390#post1951390").

---

### Post by linear on 2007-01-10
Have a look at the wiki entry [here]("https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot"), in the section headed "You lost the Yaboot menu! Now what?"

In short, if Ubuntu is on the first partition, a PRAM reset should fix the problem.

If Ubuntu is not on the first partition, hold down the option key at bootup, select your Ubuntu partition from the graphical menu, and then run sudo ybin from a Terminal after Ubuntu boots.

---

