---
title: "Toshiba U205 + Ubuntu 7.04 = No Sound"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Fliipn on 2007-06-29
Ok got a nice laptop Toshiba U205-S5022... I read and tried all the different alsa fixes and even upgraded to the latest version.. none of which worked.. (yes, I made sure the alsamixer wasn't muted) nothing seems to work..

flipn@flipn-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


flipn@flipn-laptop:~$ modinfo soundcore
filename:       /lib/modules/2.6.20-16-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     45750F13477CBA5B6F36F46
depends:        
vermagic:       2.6.20-16-generic SMP mod_unload 586

---

### Post by Zzl1xndd on 2007-06-29
Hate to ask this but I have a Toshiba m50 and I dont know if the U205-S5022 has this but mine has a old school Wheel on the front that controls the volume and I have seen a lot of people who use both LInux and Windows have sound issues and not even know it was there and just happened to be turned all the way down.

---

### Post by Fliipn on 2007-06-29
> **tweakedenigma said:**
> Hate to ask this but I have a Toshiba m50 and I dont know if the U205-S5022 has this but mine has a old school Wheel on the front that controls the volume and I have seen a lot of people who use both LInux and Windows have sound issues and not even know it was there and just happened to be turned all the way down.

It has a wheel on the side of the laptop and that works (meaning if i turn it.. I can see the volume meter change) and yes I have checked to see if it was muted (Fn + Esc) to verify that it is up.

---

### Post by scholzilla on 2007-06-29
Don't know if this will help you, but this was my experience. My sound worked fine on 7.04 until I installed the upgrades. Then the sound was disabled (see bug 121105 on launchpad for full details). It seems that one of the kernal upgrades to linux is doing this. Have you tried reinstalling, then not installing the upgrades? If this works for you, you can then  use apt-get upgrade from term to do your updates, and this won't install (for reasons I don't fully understand) the kernal updates, but will install all else. The only problem with this is I'm not sure how vulnerable you are leaving your system by not including the kernal updates.

---

