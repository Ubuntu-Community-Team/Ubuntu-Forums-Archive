---
title: "Mplayer - Full Screen Problems"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by mabase on 2006-01-17
Well I have been using Ubuntu for about 2 days, so I am a pretty big newbie. After hours of copy/pasting code and surfing these forums, I have finaly managed to get Mplayer to work. Unfortunatly, when I goto fullscreen the video is very slow. Switching the vo=x11 to vo=xv doesn't seem to work for me because when I goto play the videos I get "Error opening/initializing the selected video_out (-vo) device". My computer is using an ATI radeon x800 xl graphics card. I saw one thread the lead to hhttp://www.mplayerhq.hu/DOCS/HTML/en/video.html#vidix
but I am unable to follow the instructions (I simply don't know what to do). If someone could please help me I would greatly appreciate it.

---

### Post by otake-tux on 2006-01-17
In the prefrences box of the gmplayer menu go to video and choose xv  X11/xv.
Also what type of video are you playing?  if it is a dvd the maybe the dma is off..

---

### Post by dueY on 2006-01-17
What video card drivers are you using?  If you're using some dinky driver that came with Ubuntu that could be the problem, I recommend proprietary drivers from ATI's website.

---

### Post by kaamos on 2006-01-17
if you are using the fglrx driver, look here: [http://ubuntuforums.org/showpost.php?p=650162&postcount=4](http://ubuntuforums.org/showpost.php?p=650162&postcount=4)

---

### Post by mabase on 2006-01-17
switching the mode to xv doesnt work, it gives me the same error I previously said.  I downloaded the ati propriety driver but I do not know how to install it.  I am currently using the fglrx drivers and I dont know how to follow the instructions in the [http://ubuntuforums.org/showpost.php?p=650162&postcount=4](http://ubuntuforums.org/showpost.php?p=650162&postcount=4) post.

---

### Post by kaamos on 2006-01-17
Open a terminal and type:
```
sudo gedit /etc/X11/xorg.conf
```
There you will find a section that looks something like this:
```

Section "Device"
     Identifier "Device"
     Driver "fglrx"
*(..maybe more stuff here..)*
EndSection

```
Add the mentioned two lines after "Driver "fglrx"". So it now looks like this
```

Section "Device"
     Identifier "Device"
     Driver "fglrx"
     Option "VideoOverlay" "on"
     Option "OpenGLOverlay" "off"
*(..maybe more stuff here..)*
EndSection

```
Save the file and restart X with control+alt+backspace. When you have logged back in, try again to use the xv-output.

Hope this helps. :)

---

### Post by mabase on 2006-01-17
omgosh that worked!! Thank you so much!!!

---

