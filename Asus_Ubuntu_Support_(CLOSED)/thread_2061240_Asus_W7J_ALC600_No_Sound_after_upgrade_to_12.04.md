---
title: "Asus W7J ALC600 No Sound after upgrade to 12.04"
date: 2012-09-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Puddingfork on 2012-09-22
Laptop: Asus W7J

Audio device: ALC660

Also info: [http://www.alsa-project.org/db/?f=b2389ad9da4d2eaf6917b59e1eec27d3a5617153](http://www.alsa-project.org/db/?f=b2389ad9da4d2eaf6917b59e1eec27d3a5617153)

Other info: Sound worked with 11.04 after following these instructions
[http://ubuntuforums.org/showthread.php?t=1745179](http://ubuntuforums.org/showthread.php?t=1745179)
and adding the line suggested there
echo "options snd-hda-intel model=3stack" | sudo tee -a /etc/modprobe.d/alsa-base.conf
Upgraded via. internet to 12.04 and no longer had sound, tried that line again and it didn't work. Did a clean install of 12.04, still no sound. Tried entering that line, no sound. Since this clean install the only other change I made was activating the recommended nvidia drivers.

I've searched around a fair bit looking for a solution. From what I can tell the only solution is to downgrade my kernel, which I don't really want to do.

If anyone has anyone has any idea what I can do to fix this it would be much appreciated.

---

