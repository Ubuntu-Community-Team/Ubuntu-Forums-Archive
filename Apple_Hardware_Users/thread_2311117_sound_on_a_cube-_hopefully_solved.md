---
title: "sound on a cube- hopefully solved"
date: 2016-01-24
forum: Apple Hardware Users
---

### Post by kyle69 on 2016-01-24
My jessie/xfce cube has been too quiet... so I had to get the sound working. This led me down a bunch of red herrings of trying to understand what was going on with the soundcard driver, snd-powerpc, etc. Then I realized... there is no card on the board! It's all done through the speakers. So that wobbly path led me to: 

sudo apt-get install alsa-base alsa-utils

blacklist as desribed in [https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

In /etc/modprobe.d/ (mine had a alsa-base-blacklist.conf)
blacklist snd-aoablacklist snd-aoa-fabric-layout
blacklist snd-aoa-soundbus
blacklist snd-aoa-i2sbus
blacklist snd-aoa-codec-tas

At one point, I had put in /etc/modules a line for snd-powermac. It's actually not needed, so I commented it out. 

Here is where you make it all work. Alsa installs the usb module/driver just fine, (at least for me), so one would think it would be ok. The problem is that it assigns the usb driver to the wrong slot, as it assumes that you have an onboard card. So you need to make the usb speakers the "onboard soundcard." 

In /etc/modprobe.d/alsa-base.conf look for a line:

options snd-usb-audio...

change/delete/whatever to:

options snd-usb-audio index=0

Reboot and enjoy your new sound! You may have to tweak the volume settings by running alsamixer from a terminal window. 

HTH 

kyle


ps- if I can only get the nonfree radeon video drivers to stop freezing... may try building the drivers from source next...

---

