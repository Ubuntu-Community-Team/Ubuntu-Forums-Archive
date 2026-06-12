---
title: "USB Headset problem"
date: 2004-10-31
forum: Apple PPC Users
---

### Post by bwilson on 2004-10-31
Hi.  I'm new to Linux. I'm using Ubuntu on my G3 iBook. It's going quite well, but I have a problem with my Logitech USB headset.  Device Manager sees it in the USB section, but neither GnomeMeeting nor Sound Recorder see the headset as an input device.
How do I fix this?

Thanks.

---

### Post by oldweasel on 2005-03-08
I am also having the same issue. Is there a solution to this?

---

### Post by mips on 2005-03-11
You need to check if the USB device is your default device. If it is not you have make it your default device at the expense of loosing your onboard sound, there is a fix for this to.

See:
[http://www.ubuntuforums.org/showthread.php?t=18926](http://www.ubuntuforums.org/showthread.php?t=18926)

and to make both play at once ( have not tried this yet):
[http://alsa.opensrc.org/index.php?page=TroubleShooting](http://alsa.opensrc.org/index.php?page=TroubleShooting)
[http://alsa.opensrc.org/index.php?page=MultipleCards](http://alsa.opensrc.org/index.php?page=MultipleCards)

cheers
mips

---

### Post by icheyne on 2007-11-29
You can switch between soundcards by installing and using asoundconf-gtk

I wish USB hotplugging worked though.

---

