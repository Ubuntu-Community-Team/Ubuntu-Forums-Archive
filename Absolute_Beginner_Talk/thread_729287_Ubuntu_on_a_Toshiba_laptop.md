---
title: "Ubuntu on a Toshiba laptop"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Kendrick Hates Windows on 2008-03-19
I'm having serious trouble getting Windows out of my life. But I'm not sure if I'm smart enough to actually do it. If I can't successfully make the switch from Windows Vista to Ubuntu, I will take it as a serious personal defeat. 

Ubuntu installed perfectly on my laptop, but it is having driver problems. 

Here's my specs:

Toshiba Satellite A215

Processors: AMD Athlon 64 dual-core Tk-53
Wireless modem: Realtek RTL8187B Wireless 802.11g
Video: ATI Radeon X1200
Sound: Realtek High Definition Audio

So far I've only tried to install the drivers for the Wireless and Sound, but to no avail. Either Realtek hides their drivers somewhere deep in their website, or they don't have drivers for anything but Windows Vista.

Do you really have to use the driver from the manufacturer? or is there a generic driver for Ubuntu I can find somewhere?

I guess what my real question is, is how can I solve this problem?

---

### Post by overdrank on 2008-03-19
> **Kendrick Hates Windows said:**
> I'm having serious trouble getting Windows out of my life. But I'm not sure if I'm smart enough to actually do it. If I can't successfully make the switch from Windows Vista to Ubuntu, I will take it as a serious personal defeat. 

Ubuntu installed perfectly on my laptop, but it is having driver problems. 

Here's my specs:

Toshiba Satellite A215

Processors: AMD Athlon 64 dual-core Tk-53
Wireless modem: Realtek RTL8187B Wireless 802.11g
Video: ATI Radeon X1200
Sound: Realtek High Definition Audio

So far I've only tried to install the drivers for the Wireless and Sound, but to no avail. Either Realtek hides their drivers somewhere deep in their website, or they don't have drivers for anything but Windows Vista.

Do you really have to use the driver from the manufacturer? or is there a generic driver for Ubuntu I can find somewhere?

I guess what my real question is, is how can I solve this problem?

Hi and welcome, a quick search of the forums turned up this thread that may help
[http://ubuntuforums.org/showthread.php?t=729080&highlight=Satellite+A215](http://ubuntuforums.org/showthread.php?t=729080&highlight=Satellite+A215)

---

### Post by (((X))) on 2008-03-19
Near same specs as yours, wifi and soundcard.
Well, lets begin
It may work for you too.

There are mainly 2 guides I use for this
first is to setup wireless using ndiswrapper(wireless driver for linux)
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)


and second one is to get eveything out of my soundcard.

First I removed alsa-base and alsa-utils in synaptic.
then I got sound drivers from alsa-project.org(alsa-lib** and alsa-driver**)


Since I can't get my earphone to work properly I recompiled my kernel too
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
*NOTE 
- I used kernel 2.6.22.14 instead of 2.6.24. Because of ndiswrapper support.
- After compiling your kernel don't upgrade to newer kernel available in synaptic.
- After upgrading you have to compile alsa and wifi drivers again.

Have fun using Linux)

---

