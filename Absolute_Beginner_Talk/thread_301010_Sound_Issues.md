---
title: "Sound Issues"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by BranManSupreme on 2006-11-16
I've just installed Ubuntu 6.1 last night. It's not terribly confusing but this problem is. When I was running off the Live CD the sound was working fine and I thought nothing of it. So I create a new partition on the hard drive yadda yadda install it all in for good. Now when I get in to it, it had sound muted by default. I fiddled with the sliding bars and managed to fix that but I just don't have any sound. I right clicked the volume control and went into preferences. Selected the device to use, in my case I switch it from SAA7134 (Alsa) to Audigy 1 [Unknown] (Alsa). Audigy 1 being the name of my sound card I figured this would do it. Still, no dice. So now I'm kind of stuck with no sound and would really love to have it working. If anyone any suggestions or a solution that would be great.

---

### Post by mahy on 2006-11-16
Have you tried pressing "m" in alsamixer to mute/unmute the sound channels? If yes, have to tried loading the correct kernel module? If nothing helps you can always install newest ALSA from sources.

---

