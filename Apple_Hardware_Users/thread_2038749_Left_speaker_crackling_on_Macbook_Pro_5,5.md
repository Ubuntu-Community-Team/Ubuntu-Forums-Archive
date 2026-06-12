---
title: "Left speaker crackling on Macbook Pro 5,5"
date: 2012-08-07
forum: Apple Hardware Users
---

### Post by butchertkd on 2012-08-07
Hello, I have a Macbook Pro 5,5 running Linux Mint 13 now, but I have this issue also in Ubuntu 11.04, Ubuntu 12.04 and Debian Squeeze (these are the distributions I tried). I am using Ubuntu on this macbook for two years but the problem has appeared  two/three months ago, when once I turned the volume over the 100% in the Sound Preferences (PulseAudio), and from that moment I can't resolve it. The speaker is working properly under OS X, thus it's not broken. I have tried with this [http://ubuntuforums.org/showthread.php?t=1057879](http://ubuntuforums.org/showthread.php?t=1057879) ... also tried adding this in /etc/modprobe.d/alsa-base.conf ...
options snd-hda-intel model=intel-mac-v5 position_fix=2 probe_mask=1 also tried with model=mbp55 ....
I also tried with a different kernel cause Debian squeeze was running 2.6.something I think...
Do you have any idea how could I solve this? 
 [http://pastebin.com/ckb99a3g](http://pastebin.com/ckb99a3g) here my alsa-info obtained with this script [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) ...If you need some other informations just ask me..

Thank you

---

### Post by 2blue on 2012-08-07
I am in lubuntu right now, and there is no pulse audio for me to check what kind of settings there are. It might still be worth opening alsamixer in termial and play around with settings there if you haven`t already.

---

### Post by butchertkd on 2012-08-07
Thanks for the answer, but I don't think the problem is because of PulseAudio. If I try with debian Squeeze XFCE I have the same issue, and it's without PulseAudio and yes I have already checked all the pulse audio and alsa settings in the mixer....I really can't understand which is the cause...

---

### Post by butchertkd on 2012-08-20
I have the same issue with Fedora 17.  I have also tried with Ubuntu 8.04 and there is no sound at all there, probably because the driver of this sound card wasn't yet written. I've also tried with some different options in /etc/modprobe.d/alsa-base.conf  looking here [http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt](http://www.kernel.org/doc/Documentation/sound/alsa/HD-Audio-Models.txt) . Same problem with all model I have tried, but with "auto" where I have no sound at all with that. Could it be some problem with alsa?? Is there anything I can try to find the source of the problem??

Thanks again.

---

