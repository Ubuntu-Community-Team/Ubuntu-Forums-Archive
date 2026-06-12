---
title: "VLC Player cannot play any videos!!"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-02-29
Nothing works!

What happens is, when I insert a DVD and play it through VLC, VLC opens.. then about 1 second later, it closes.... What?! (Also this happens when trying to play any type of video (AVI, Div etc))
When I had Windows, VLC player worked perfectly. 

Why won't it play any video?
How do I fix it?


Thanks,
Tom

---

### Post by jan quark on 2008-02-29
do you have installed the codecs needed for viewing the dvds?

see here:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29%7C%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29%7C%28restricted%29)

also try to run vlc via the terminal.

```
vlc
```
are any error messages displayed?

---

### Post by Tom--d on 2008-02-29
```
tom@Laptop:~$ vlc
VLC media player 0.8.6c Janus
tom@Laptop:~$ 
```

Then the vlc player opened. so that works. Just no videos. DVDs and avi and all that etc

---

### Post by Tom--d on 2008-02-29
Ah. Videos now work :D

But no DVD yet.

---

### Post by jan quark on 2008-02-29
```
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
```

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

run this in terminal as suggested in the wiki and open the dvd with the application gxine

---

### Post by Tom--d on 2008-02-29
Yay :D 
It works!!

Thanks :)

Also, How do I make VLC player default for ALL videos and DVDs (NOT music tho)

---

### Post by herbster on 2008-02-29
You can do that by opening a file browser and right-clicking a video file, say a .avi, click Properties > Open with tab > select VLC if you see it in the list, otherwise click Add and find VLC in that list, hit Add, then select VLC in the list and hit Close. Then .avi files will open with VLC. You'd have to do that for .mpg, .mov, .mkv, etc. if you want them all to open with VLC.

---

### Post by Tom--d on 2008-02-29
> **herbster said:**
> You can do that by opening a file browser and right-clicking a video file, say a .avi, click Properties > Open with tab > select VLC if you see it in the list, otherwise click Add and find VLC in that list, hit Add, then select VLC in the list and hit Close. Then .avi files will open with VLC. You'd have to do that for .mpg, .mov, .mkv, etc. if you want them all to open with VLC.

I've done that but when I open the file after, it still opens it with a different player.

---

### Post by herbster on 2008-02-29
You're probably missing a step then, right-click on a video file and hit Properties, go back to the Open With tab and make sure VLC has the radio box highlighted on it. I did the same thing with not having the file highlighted although I had added it to the list. That may be it.

---

### Post by Tom--d on 2008-02-29
Ah, Done it :)

Thanks!! :KS

---

### Post by herbster on 2008-02-29
Excellent! :) Mark your thread as solved for others :)

---

