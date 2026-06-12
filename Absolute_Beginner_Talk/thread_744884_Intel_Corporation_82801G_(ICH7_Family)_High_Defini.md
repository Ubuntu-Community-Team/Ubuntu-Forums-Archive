---
title: "Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-04-04
Hi
Thank you for reading my post
Does any one has an audio cart similar to mine?
I want to borrow a copy of your sound system configuration file, it is located at /var/lib/alsa/asound.state
It may help me to make my sound system works properly.

to be more specific, when you type ```
 aplay -l 
``` in your command console you may get 
```

card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1

```

which means that our cards are the same.
Thanks

---

### Post by bilal.17 on 2008-04-04
i have exactly the same card on my laptop.. and only the sound works... the microphone will not... this is a very common problem and is documented throughout the forum frequently... the only solution to the mic problem is to use a usb microphone

---

### Post by bilal.17 on 2008-04-04
ive also noticed that some people dont even get the sound to work with their card... you can try to install the latest alsa drivers.. if that doesnt work, then i think you might be out of luck

---

### Post by legolas_w on 2008-04-05
Would you please share the content of /var/lib/alsa/asound.state?
I have a good sound quality and it suddenly changed to a very bad sound quality. I think something went  wrong somewhere, I even reinstall the alsa-base and alsa-utils with no luck.


thanks

---

