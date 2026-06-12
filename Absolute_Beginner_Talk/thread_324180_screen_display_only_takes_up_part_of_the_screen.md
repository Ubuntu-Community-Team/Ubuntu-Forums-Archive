---
title: "screen display only takes up part of the screen"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by emu on 2006-12-23
hi,

when I tried to run the liveCD of Ubuntu (Dapper Drake) on a Dell Latitude D800, the display took up the whole screen except it was doing weird things (some lines of pixels were flickering and it was broken into three columns that didn't match up).  so I ran it instead in 'safe graphics mode' and it looked fine, except for that the image only uses about 3/4 of the screen (it's centered, the whole image is there except it's just small, and the rest of the screen is just a black border).

so I went ahead and installed anyway, but the screen display is still smaller than the actual screen.  is there any way to get it to recognise that the rest of the screen is still there?  any help is very much appreciated.

---

### Post by Scorpuk on 2006-12-23
What resolution are you running linux at and what's the maximum resolution the screen can do natively?

---

### Post by emu on 2006-12-23
ubuntu resolution : 1024x768 (in the screen resolution preferences there is no option for a resolution higher than this)
laptop resolution : 1920x1200

---

### Post by Scorpuk on 2006-12-23
ooo nice laptop btw.


what you might want to do is edit the xorg.conf file to add in the resolution you want. I had to do this for my box to get 1280 x 1024.


```
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
```


Open up a terminal window and type


```
sudo gedit /etc/X11/xorg.conf
```


and add in the resolution you want to the 24 bit section.


so you end up with 

```
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
```


The reason you have the border is that the screen is 1920 x 1200 and only that. any other seolution will just show up as a smaller screen inside this range. Try 800 x 600 and see what you get. If I'm right it shoudl be a smaller windows with bigger black borders. If I'm wrong then don't try what i suggested. :D


EDIT: don;t forget to add in the resolutions for all the other colour depths. ;)

---

### Post by emu on 2006-12-23
that worked, thanks so much!

---

