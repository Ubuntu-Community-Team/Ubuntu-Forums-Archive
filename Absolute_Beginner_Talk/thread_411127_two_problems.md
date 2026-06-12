---
title: "two problems"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-04-16
i have two problems, first on my tohshiba latop i can't install the restricted codecs, i have tried using the terminal , and by installing the packages individually from medibuntu, and the gdebi package installer will not install. it says that the unpacked data will bigger than the packed data. i know that and i when i respond that yes it's ok it responds, abort.

second i have a nvidia driver in my desktop, and i can't install beryl. i downloaded and installed to nvidia drivers but when i set beryl as my window manager, it acts like it tries but gives up and metacity wins. the tops of the windows flash and then return to normal no wobbles or nothin.........:confused:

---

### Post by crosintoski on 2007-04-16
I don't know about your first problem but for the second try this:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

---

### Post by annda on 2007-04-16
can you copy and paste the exact message you get in the terminal after this command:

```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs 
```

(it's from [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs))

(copy in the terminal: CTR+SHIFT+c)

---

### Post by rickycodie on 2007-04-16
> **crosintoski said:**
> I don't know about your first problem but for the second try this:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

i tried it and must have messed something up cause now my video doesn't work. yay.
how do i restore my settings ?
never mind i got it fixed.

---

