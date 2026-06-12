---
title: "Xubuntu DVD playback"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by smurphv2 on 2007-11-27
Hey all. Using Xubuntu 7.10 here, and am having trouble w/DVD playback. I used this guide [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability")

which has not allowed me to view encrypted DVDs. I've browsed the forum looking for suggestions, and nothing has worked thus far. I have tried using vlc, xine-ui, and totem. In totem and xine, the DVD will start playing, and eventually come up with an error message. In VLC, after picking a chapter, the video will not play at all. If anyone has any suggestions, I would appreciate it. Feel free to ask for any more information. Thanks.

---

### Post by PeterJS on 2007-11-27
You want Medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and you want the packages:
[i]libdvdcss2
libdvdread3[/i]

---

### Post by smurphv2 on 2007-11-27
Thanks for the reply. Unfortunately, I believe that all been done already.

```
sudo apt-get install libdvdcss2 libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
libdvdread3 is already the newest version.
The following packages were automatically installed and are no longer required:
  libmozjs0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Any other suggestions?

---

### Post by smurphv2 on 2007-11-27
self-serving bump

---

