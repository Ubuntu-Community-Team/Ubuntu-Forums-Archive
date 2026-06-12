---
title: "sound playback jerky"
date: 2007-02-21
forum: Apple PPC Users
---

### Post by rol1 on 2007-02-21
I have a 500mhz g3 ibook, the "icebook". 

I am using VLC to playback KPIG's 64 bit AAC stream.

when it first starts it plays fine, but if I use the mouse or arrow keys too much the sound really breaks up and continues till I stop and restart the stream.

I have played around with the VLC priority setting in VLC preferences but that hasn't done much.

Is there other settings that I can adjust to give the sound a higher priority?

It is not a matter of bandwidth, it does it with the 128 and 24 bit streams, and I have have several computers running streams with no problems, till I scroll down the page I'm reading.

I'm thinking that mouse and keyboard uses up processor causes the stream to be interupted.

---

### Post by rol1 on 2007-02-24
I have tried to set renice to -10 for the VLC and mixer processes shown in > ps -u rol1 but doesn't make a whole lot of difference.

In top, what is the "id" stand for in cpu field of the summary area? This is running 80 to 90 percent

---

### Post by maggot_brain on 2007-02-24
The G3 ibooks have poor floating point performance.  This is probably what's causing it.  I doubt there's much you can do about it.

---

### Post by rol1 on 2007-03-02
Well, its been a few days now and I haven't had to restart VLC to get the sound back proper.

I opened the program top in a terminal window, used the "r" key to renice Firefox to a +4 and had allready reniced VLC to something like -15. Now I can play the Kpig stream without it sounding like someone is playing with the volume. It was really annoying to have to keep going back to VLC and start and stop it every time I forgot to use the function key/page down combo to scroll down a webpage.

Now I can use the arrow keys and trackpad without interuption.

---

### Post by rol1 on 2007-03-06
I went ahead and reniced VLC back to 0 and it seems that renice'ing firefox to a +4 is enought to stop the breaking up of stream playback in VLC. So I guess now I need to get rid of libflash that I install by misunderstanding. And  IBM's Java needs to be installed. But as long as I got KPIG stream going it doesn't seem as urgent.

---

