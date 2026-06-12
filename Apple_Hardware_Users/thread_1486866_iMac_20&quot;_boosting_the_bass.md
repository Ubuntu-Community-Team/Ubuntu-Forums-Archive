---
title: "iMac 20&quot;: boosting the bass"
date: 2010-05-18
forum: Apple Hardware Users
---

### Post by pigreco on 2010-05-18
I've installed Ubuntu 10.04 on an iMac 20" (early 2009). I had success in making the sound work. While the quality through the earphone is very good, the same does not hold if I use the internal speakers. In fact, in this case the sound is very tiny. I suppose that the integrated subwoofer does not work in Ubuntu. Is there any trick to get a better sound, namely with more bass?

---

### Post by linuxopjemac on 2010-05-18
According to my [news post of 17.02.2010]("http://mac.linux.be/content/more-apple-improvements-kernel-2633"), there will be better audio support for the iMac 9,1 in kernel 2.6.33. In the alsa config file you should be able to add imac91. I guess, that if you add the alsa backport in Lucid, you will be able to enjoy this feature.

[http://packages.ubuntu.com/lucid/main/linux-backports-modules-alsa-lucid-generic](http://packages.ubuntu.com/lucid/main/linux-backports-modules-alsa-lucid-generic)

Add 
```
model=imac91
```
to /etc/modprobe.d/alsa-base.conf


Let us know if it works...

---

### Post by pigreco on 2010-05-18
Thanks for your reply. How should be installed the patch, attached to the link you posted?

---

### Post by linuxopjemac on 2010-05-18
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```

then:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
then add the model at the end, it probably has something like:

```
options snd-hda-intel power_save=10 power_save_controller=N
```

Add it after this, so
```

options snd-hda-intel power_save=10 power_save_controller=N model=imac91
```

then CTRL-X and "y" to save
then reboot
hopefully it works then

---

