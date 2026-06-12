---
title: "PC speaker remains ON when i connect headphone"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by alobnok on 2007-03-15
Hi Everybody,

I have a Toshiba A135-4447 laptop and have installed Ubuntu as dual boot with Vista. Today when i was playing my music and listening it using my headphone, i noticed that even though my headphone was working but my laptop speakers were also on.

Can anybody tell me how to stop the laptop speakers when i am using the headphone.

Regards

Vikas

---

### Post by Jonam on 2007-03-16
Try using the Volume control in Ubuntu by right-clicking on the speaker icon next to the date in the top right corner of your screen and selecting "open volume control". You should see a couple of sliders. Experiment with these to see what happens. 

Jonam

---

### Post by Kobalt on 2007-03-16
There is also a little trick you might be able to use : on my HP laptop the soundcard wasn't properly working on Edgy and at the begining of Feisty, now it's ok and I finally get to use my headphones. However, like you, when I plug them in the speakers remain active. To turn them off I press 'mute', then all sound goes off. I press it once again and the sound only comes back through headphones... 
Hope it's helpful.

---

### Post by WickedAwsome on 2007-03-18
I have essentially the same laptop and the above suggestion did not work for me, any further ideas?

---

### Post by annda on 2007-03-18
the Intel HDA is not fully supported by ALSA at the moment (at least in this annoying aspect).

some people report success with booting with theis headset plugged in.

others are able to activate a "sense headphone jack" option when they enable extra options in the volume manager.

some cards can be "tweaked" by extra ALSA options. take a loot at this post:
[http://ubuntuforums.org/showpost.php?p=1986146&postcount=11](http://ubuntuforums.org/showpost.php?p=1986146&postcount=11)

---

### Post by aquameta on 2007-03-19
Upgrade your kernel.  I have the same problem and haven't tried this fix but read that it works:
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/36512](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/36512)
[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/35098](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/35098)

---

### Post by FuriousLettuce on 2007-03-25
I have an HP laptop with an Intel ICH6, and originally my speakers were staying despite the headphones being in. To fix it, I right-clicked on the volume control, went to "Open Volume Control". Go to Edit -> Preferences, and make sure the option "Headphone jack sensor" is ticked, then click OK. Next, go to the "Switches" tab, and tick the one that says "Sense headphone jack", and everything should work fine (hopefully). Did for me at least...

---

