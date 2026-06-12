---
title: "Left Audio Channel Distortion -"
date: 2007-07-01
forum: Apple Intel Users
---

### Post by linkx on 2007-07-01
My left audio channel is all crackly - this is the case on every distro or kernel I try. Sounds fine in OS X and Windows. Just installed Ubuntu Studio and it was fine--until I just opened the Sound preferences, where it became immediately garbled, just like the other 12 distros I have installed. 

The left audio channel works but is distorted, while the right sounds great. It happens at all volume levels, speakers AND headphones, and sounds just fine when in OS X or Windows.  


Please HELP!

Thanks

---

### Post by filologen on 2007-07-01
I have occasionally had the same  problem on my MacBook Pro (1. gen.)

This solution worked for me:

sudo rmmod snd_hda_intel
sudo modprobe snd_hda_intel

(You remove the hda_intel extension from the kernel and then add it again)

You probably have to kill one or more processes which are using the extension. For me it was enough to kill the process "mixer_applet2".

Hope it will work out for you as well :-)

---

### Post by linkx on 2007-07-01
Thanks! I'm not sure which processes I need to kill. Seems like no matter what I do I get:
```

ERROR: Module snd_hda_intel is in use

```

Is there any way I can tell which process is using this?

---

### Post by linkx on 2007-07-01
I just booted into recovery mode and ran it there. PERFECT! THANK YOU SO MUCH! I've been complaining about this for months; the day I finally quit complaining and posted is the day it got fixed! YES!

---

### Post by filologen on 2007-07-02
You are very welcome! Glad it worked out for you as well :-)

---

