---
title: "No Midi"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by yelserpdog on 2007-05-04
x

---

### Post by fenian on 2007-05-04
You can try installing the low latency kernel from [these instructions]("https://wiki.ubuntu.com/RealTime").

or you can try to use timidity from[ this wiki.]("https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo")  

to set the frequency to a more appropriate setting for midi use this command....

>  sudo sysctl -w dev.rtc.max-user-freq=1024

to make that change consistant across reboots use this command...

>  sudo su -c 'echo dev.rtc.max-user-freq=1024 >> /etc/sysctl.conf'

---

