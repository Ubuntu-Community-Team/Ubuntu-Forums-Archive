---
title: "Can I restore everything related to audio to the original version?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by samuraiCat on 2007-06-24
Hi, everyone. Thanks in advance.

Okay, I installed Ubuntu, and I got my Lexmark Z517 printer and nVidia GeForce FX5200 video card working great. 

But I completely screwed up my audio stuff. 

See, I physically installed a M-Audio Revolution 5.1 card, and then immediately installed the OSS drivers that M-Audio linked to via 4-Front technologies. Then I read about ALSA, and I tried to follow the instructions on the following thread unsuccessfully: M-audio Revolution and upgrade Alsa ([http://ubuntuforums.org/showthread.php?t=400268](http://ubuntuforums.org/showthread.php?t=400268))

The instructions did not work for me, especially at the end: 

> If you have any other cards (like an onboard card), you can add it to --with-cards seperated by commas. After the installation is finished, do a complete reboot. Then run
Code:

cat /proc/asound/version

to check if you successfully upgraded Alsa. The first time you reboot after upgrading Alsa or installing a new system, you must increase the volume of all channels in alsamixer.

After all that, there was no such directory as "/proc/asound/version".

Then I tried to use Hydrogen and Alsamixer, and neither of them would load! Alsamixer gave this weird warning: "alsamixer: function snd_ctl_open failed for default: Nos such device"

I uninstalled all my audio programs and drivers, reinstalled, and still nothing. 

So then I went into User Panic: I downloaded everything related to ALSA via Synaptic. I made countless tweaks to various files. I don't even know what I did.

Nothing changed. I can play movies and music with the media players, but none of the other stuff works.

So, now I want to go back to the original and start again, as if I had just put my card into the slot. Is there a way to do this? Thanks.

---

### Post by mikewhatever on 2007-06-24
You can try the following, here is the source page [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
> Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

[list][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop



---

### Post by samuraiCat on 2007-06-24
> **mikewhatever said:**
> You can try the following, here is the source page [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) 

Okay, thanks, but will this fix all the sourcecode changes I made? Is this like XP, when you change something in a driver or file it can cause a bunch of other apps to stop working correctly?

---

### Post by mikewhatever on 2007-06-25
> **samuraiCat said:**
> Okay, thanks, but will this fix all the sourcecode changes I made? Is this like XP, when you change something in a driver or file it can cause a bunch of other apps to stop working correctly?

I hope so.;)

---

### Post by samuraiCat on 2007-06-25
> **mikewhatever said:**
> I hope so.;)


UPDATE: Oh, crap. From [http://www.linuxdevcenter.com/pub/a/linux/2001/05/17/drivers_2-user.html](http://www.linuxdevcenter.com/pub/a/linux/2001/05/17/drivers_2-user.html)
> You can't get the performance you desire from the current driver and want to try another one.

This is potentially the trickiest scenario to manage. Each of the available driver packages maintains a different presence in your system startup and filesystem. If your existing driver is modular you can simply remove it from /lib/modules/linux-version/sound; however, if the driver is hardcoded into the kernel you will to recompile the kernel for modular sound support. You must have a kernel set up for modular sound if you want to use the ALSA drivers (just don't select any specific driver when configuring the kernel). The 4Front package installation routine can be directed to uninstall any kernel sound modules (but not ALSA modules) before installing OSS/Linux; a reboot is not required.

I'm going to have to totally reinstall Ubuntu again, aren't I? Crap.

---

