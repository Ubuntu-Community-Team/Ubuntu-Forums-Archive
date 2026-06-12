---
title: "How do you get the Totem Movie Player To Play WMV"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by JayDeePlus on 2007-04-13
i have the Totem Media Player, and i was wanting to watch something thats a .wmv. when i try to play it , it say that i don't have the correct decoder. where or how do i get the right decoder?

---

### Post by yabbadabbadont on 2007-04-13
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by JayDeePlus on 2007-04-13
ok i think i got it to load the file, but the video is not showing, it's just the sound playing. i followed those instructions on the link you gave me those and put in a code into the temrminal and it loaded everything. but the video don't play.

---

### Post by yabbadabbadont on 2007-04-13
If the wmv file uses Windows DRM, you may not be able to play it in Linux...  :(

You might try installing mplayer or xine-ui with the w32codecs.  Others swear by vlc for playing such files.  It all seems to be rather hit and miss when it comes to wmv files.  :?

---

### Post by JayDeePlus on 2007-04-13
well i even tried to install that desk session recorder, and like it want play the video. some times when i try to save it, the window just close. any suggestions?

---

### Post by ghansel on 2007-04-13
Use VLC! It plays everything and everything.

```
sudo apt-get vlc ffmpeg
```

---

### Post by JayDeePlus on 2007-04-13
how do you change what media program will open up with? like change from media player to realmedia or VLC? everytime i open a link to something i want to watch media player opens it, and this is from the net so i can't right click and go to open with option.

---

### Post by 3ntity on 2007-04-17
> **ghansel said:**
> Use VLC! It plays everything and everything.
Not really. See attached screenshot, running VLC 0.8.4. This **video** plays fine in Kaffeine...

---

### Post by seetho on 2007-04-17
You can use gxine to play most formats that somehow totem is not able to play.  You must install gxine, libxine1, libxine-extracodecs.  

Then you want to go to [http://www.mplayerhq.hu/design7/dload.html#binary_codecs](http://www.mplayerhq.hu/design7/dload.html#binary_codecs) and download the appropriate binary codec package for your platform.

Unpack the contents into a temporary directory e.g. $HOME/temp/
sudo mkdir /usr/lib/win32
sudo cp $HOME/temp/*.* /usr/lib/win32/

You're done now.  Start gxine and play your wmv files.

---

