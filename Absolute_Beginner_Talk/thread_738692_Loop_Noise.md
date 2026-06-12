---
title: "Loop Noise"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by PollitowuzHere on 2008-03-28
After successfully  installing Ubuntu, I have a sort of loop noise in the background. Any idea on how to disable it? I did have to input "Linux= no aipc" to get the desktop to show when I installed it, and the noise was present then.

---

### Post by kool_kat_os on 2008-03-28
what does a loop noise sound like?

---

### Post by PollitowuzHere on 2008-03-28
its hard to describe, its like a twu sound

---

### Post by PollitowuzHere on 2008-03-29
Well, just tested it again and I can hear the last sound played, which means a beep is repeated over and over ad nauseum. Any help with that?

---

### Post by spiderbatdad on 2008-03-29
could you post your /boot/grub/menu.lst
I'm thinking you have some accessibility feature for the blind enabled by default in the boot process.

could you also post /var/log/dmesg after boot?

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/80535](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/80535)

---

### Post by The_PHP_Jedi on 2008-03-29
I've also experienced the noise on my desktop, but it is not directly caused by hardware. In my case, it is not constant. It only occurs when there is video playing, or in some cases, images.
It seems to be linked somehow to something that involves the updating of the screen, since I've only noticed the noise when the screen has moving elements (moving windows, certain compiz-fusion effects, boot-up loading bar, etc).

I do get the noise generally when starting up the OS, after the sound drivers are loaded. It continues until the login screen shows up and then stops. Once you log-in, it starts again until everything is loaded.

I am also using compiz-fusion, and experience the noise when most effects are triggered (specifically the ones that involve movement of elements within a desktop).

Also the noise is only heard through the speakers, so it's not produced by hardware itself. It _could_ be some sort of hardware interference, but that's jumping to conclusions without much debugging.

Hope you can help both of us.

---

### Post by PollitowuzHere on 2008-03-29
Ok, posted both items here: 
/boot/grub/menu.lst : [http://slexy.org/view/s2LRgAbV00](http://slexy.org/view/s2LRgAbV00)
/var/log/dmesg: [http://slexy.org/view/s201QZ39bb](http://slexy.org/view/s201QZ39bb)

---

### Post by forrestcupp on 2008-03-29
It happens even when you reboot?

---

### Post by PollitowuzHere on 2008-03-29
Yes, it happens after I reboot, all the time since installation actually

---

### Post by Stason on 2008-04-04
It also happens on my system. Although it is present when the system is idle. If you do something it disappears. I have integrated nvidia sound. Any hlp would be appreciated. It is qite annoying, so I have to turn off the speakers.

---

