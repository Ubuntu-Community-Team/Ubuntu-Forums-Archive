---
title: "what totem plugin do i need to ply mpeg?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2007-03-22
for some reason when i open VLC player beryl closes it rite away. totem movie player works, put dosent support mpeg files. what plugins do i need to install so it will play mpeg?

---

### Post by seshomaru samma on 2007-03-22
for totem plugins
```
sudo apt-get install totem-gstreamer-firefox-plugin
```

make sure you have all these:
```
sudo apt-get install libxine-extracodecs 
sudo apt-get install gstreamer0.10-ffmpeg
 sudo apt-get install gstreamer0.10-gl 
sudo apt-get install gstreamer0.10-plugins-base sudo apt-get install gstreamer0.10-plugins-good sudo apt-get install gstreamer0.10-plugins-bad 
sudo apt-get install gstreamer0.10-plugins-bad-multiverse 
sudo apt-get install gstreamer0.10-plugins-ugly sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by da1nonlymikeo on 2007-03-22
ah that works. thankss :)

---

