---
title: "Nvidia 8500 - Driver problems."
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Schwooter on 2008-03-04
Alright, so, here's the situation. I'm on my fourth re-install of Ubuntu. I've used Windows my entire life, so Linux is a bit overwhelming for me, and I'm a bit lost. My friend has been leading me through everything, mostly. The only problem I've had (so far) is that I can't use my video card, which is a Nvidia 8500 GT Geforce. I've tired using a script called "Envy", which automatically installs drivers for either Nvidia or ATI. I choose Nvidia, and I was still having problems. I've tried using the restricted drivers, and that doesn't work.

When I use "nvidia-glx-new" (which comes in all of the drivers that you can automatically install with Envy, or manually install with Envy. Even the restricted driver uses it.) and I reboot my machine, the Ubuntu logo comes up, the loading bar goes through, and then I get a black screen. I have a Samsung SyncMaster 997DF, and there's a small light on it that stays on when the computer is on. When the computer goes off, and the monitor is still on, this "on" light blinks on and off. When I boot up Ubuntu, and after the loading screen, the light starts blinking.

Now, since this is my fourth attempt (from messing with stuff in Ubuntu, not really knowing what I was doing, I've made Ubuntu unstable and had to reinstall. Don't ask me how I did it.), I know a few things on how to get back to my desktop (Using "sudo dpkg-reconfigure -phigh xserver-xorg" or without the "-phigh".). This time around, all I've installed is XMMS and Flash, and haven't used XMMS (Haven't installed sound drivers yet. It's a Sound Blaster Audigy, if you want to help me with that, too.). I also haven't installed the 196 updates this time, yet. The other times, I have.

I believe that's all there is to cover. If someone needs further specifications, please tell me right away.

Hopefully I'll get somewhere this time.
-Thomas

EDIT: Currently, I'm downloading the 196 updates overnight. I hope it doesn't affect anything.

---

### Post by hoges on 2008-03-04
Well, the flashing on the monitor usually means that the monitor is getting a signal it can't handle. Mine usually comes up with an error message on screen as well, but i don't think all models do this.

Have you tried downloading the latest linux drivers from Nvidia? I think there's a forum how-to somewhere to do this.

As for the SB Audigy - you may be out of luck. I still can't get my X-Fi working properly. Creative don't like linux much...

---

### Post by Schwooter on 2008-03-05
> **hoges said:**
> Well, the flashing on the monitor usually means that the monitor is getting a signal it can't handle. Mine usually comes up with an error message on screen as well, but i don't think all models do this.

Have you tried downloading the latest linux drivers from Nvidia? I think there's a forum how-to somewhere to do this.

As for the SB Audigy - you may be out of luck. I still can't get my X-Fi working properly. Creative don't like linux much...

Well, the Envy script I was talking about is pretty much a search-bot (I think...) and it just finds the latest drivers for your card. I might be wrong.

I'll go find the latest Nvidia drivers, though. I'll keep you updated.

---

### Post by hoges on 2008-03-05
I just found this link from may last year on the forums. Seems that it worked out for them...
[http://ubuntuforums.org/showthread.php?t=453586]("http://ubuntuforums.org/showthread.php?t=453586")

---

### Post by Schwooter on 2008-03-05
> **hoges said:**
> I just found this link from may last year on the forums. Seems that it worked out for them...
[http://ubuntuforums.org/showthread.php?t=453586]("http://ubuntuforums.org/showthread.php?t=453586")

I'll mess with it tomorrow. Seems possibly promising, however, they're using a different version of Ubuntu (7.04). I'm going to go to sleep, and install those 196 updates overnight.

---

### Post by Schwooter on 2008-03-05
Alright, back from sleep. The updates installed fine.

However, I was looking at that link, and it seems they're using Feisty Fawn and not Gutsy Gibbon.

Anyone have any idea on what to do?

---

