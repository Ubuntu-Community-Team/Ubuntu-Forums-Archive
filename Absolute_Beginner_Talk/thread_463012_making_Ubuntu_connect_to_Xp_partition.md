---
title: "making Ubuntu connect to Xp partition"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by mAkKoOo210 on 2007-06-03
Is there any way to make my Ubuntu programs use the Data in the Xp partition?
Make Amarok read the mp3s or the playlists...or allow the images in that partition to be used as Desktop  wallpaper...
Please answer:D

Xp partition is NTFS

---

### Post by gerscht on 2007-06-03
Is the partition mounted (e.g. can you see it on your desktop)?
post 
```

sudo less /etc/mtab

```

---

### Post by mAkKoOo210 on 2007-06-03
yes, it is mounted, I can see it. But now I can listen to music only using the video player, for example....

---

### Post by gerscht on 2007-06-03
You mean by double clicking the file?!

Try right click and select the application you want to open it with....
There is an option to use this program as default.

---

### Post by mAkKoOo210 on 2007-06-03
Double clicking the file I only get a window where it is said if I want to run in terminal, display, cancel or run the executable text file...that is a m3u playlist!
Trying to launch an mp3 or a playlist with amarock (right-click--->open with amarok) the program says "playlist finished" without playing a second...

---

### Post by gerscht on 2007-06-03
Do you have the restricted codecs installed (see: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624) )?

---

### Post by mAkKoOo210 on 2007-06-03
yes, but it still doesn't work:(

---

