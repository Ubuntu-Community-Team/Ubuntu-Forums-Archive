---
title: "no audio thru built-in speakers: ubuntu 9.1 on iMac"
date: 2009-11-03
forum: Apple Hardware Users
---

### Post by skinnerg on 2009-11-03
I'm having a problem getting any audio through built-in speakers on iMac booting into kubuntu (9.1).  I can get sound through headphones just fine.

I have tried commenting out the line:

    options snd-hda-intel power_save=10 power_save_controller=N

in /etc/modprobe.d/alsa-base.conf as I've seen suggested and have added:

    options snd-hda-intel model=imac24

both to the end of alsa-base.conf and also in a file options.conf in same location.

I have also tried using isight-firmware-tools (as advised here: [https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight)) to get the firmware from OSX (10.5.8) but it failed along the lines of other users reporting errors (at [https://bugs.launchpad.net/isight-firmware-tools/+bug/420834](https://bugs.launchpad.net/isight-firmware-tools/+bug/420834))

Could anyone give me any pointers to try next please?
Thanks!

---

### Post by zacbarton on 2009-11-04
Tho I dont see this as a fix you should get sound using:

options snd-hda-intel model=mbp3

I'm using the patch found here (comment 3):

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/346170)

---

### Post by skinnerg on 2009-11-05
Thanks zacbarton - I installed the patch as you suggested and eventually got it working after changing the channel mode to 6ch.

---

