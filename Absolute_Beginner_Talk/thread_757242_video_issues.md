---
title: "video issues"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-04-16
i am using ubuntu ultimate 1.7 edition.initially,all the players were playing videos very well,but now they are not.the problem showed up in the middle of a playback on VLC.but now none of the players play videos,the audio track plays,but instead of the video,the area of the screen where the video is supposed to play is covered with green patches.i had encountered this problem even before,and i was jolted into reinstalling ubuntu ultimate,which did solve the problem.but i get the same problem again.i believe it is not something of a hardware problem as i never face such a problem with windows.

---

### Post by crjackson on 2008-04-16
> **stonecoldjha said:**
> i am using ubuntu ultimate 1.7 edition.initially,all the players were playing videos very well,but now they are not.the problem showed up in the middle of a playback on VLC.but now none of the players play videos,the audio track plays,but instead of the video,the area of the screen where the video is supposed to play is covered with green patches.i had encountered this problem even before,and i was jolted into reinstalling ubuntu ultimate,which did solve the problem.but i get the same problem again.i believe it is not something of a hardware problem as i never face such a problem with windows.

Here, try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

BTW - You shouldn't be posting 2 threads back to back with the same issue...

---

