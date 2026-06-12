---
title: "No sound coming out from the headphones on a Macbook 5,2"
date: 2014-01-13
forum: Apple Hardware Users
---

### Post by canhoto on 2014-01-13
Can anyone help solving a problem on a Macbook 5,2 running Linux Mint 16 (actually, Ununtu 13.10), in which no sound comes out from the headphones nor external loudspeakers? I tried to change things in Alsa Mixer and Sound settings, but with no luck. It does mute the built-in speakers and it recognizes the phones (in the sound settings), but no sound comes out from it.

I tried lots of possibilities of changing /etc/modprobe.d/alsa-base.conf , namely those suggested in this thread, which should work:

[http://ubuntuforums.org/showthread.php?t=1370252](http://ubuntuforums.org/showthread.php?t=1370252)

But the result is always the same: 
- when I plug in the headphones/earphones, the built-in speakers are muted, but there's no sound from the headphones
- in alsamixer the Headphones column is automatically unmuted and put to a high volume; but nothing comes out; I tried to unmute and increase the volume level of all the sliders (speakers, PCM, master, etc.) but no success: still no sound from the speakers

The chipset is a Realtek ALC889A.

BTW, I have another Macbook (2,1) running Elementary OS Luna (based on Ubuntu 12.04.3) and it runs out of the box


Any help, please?

---

