---
title: "Graphics Corruption (Live CD 64 bit)"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by newo on 2006-01-31
Well, thanks to the help of the forums, I managed to burn the Live 64bit CD and boot it up. However, once everything has loaded up and it goes to the main desktop there's serious graphics corruption error and I can't see anything at all. 

I have a 64 bit system (Athlon 64bit 2800+) so I don't think that's the problem. The next possible reason I can think of is that my graphics card (Nvdia 6600GT) is not supported, is this the case? 

I'm now downloading the 32 bit Live version too see if that works, in the mean time has anyone encountered graphics corruption during boot-up and know a fix?

Thanks!

---

### Post by rusacarr on 2006-01-31
I have run across some of the same issues.  Also running AMD64 (3200) and Kubuntu 5.10, installed from the LiveCD.  

I do not really have corruption on the login screen, but corruption during standard run time is becomming a common occurance.  I do not totally feel it is your video card, since I run a trashy SiS based card, not an nVidia.  Maybe new drivers?

Any other ideas?

---

### Post by newo on 2006-02-01
Well, I've not found a solution unfortunately, and I don't intend to attempt to install Ubuntu in case the corruption comes up in the install too.

Oddly enough, the Live 32 bit CD does work on my other PC ( a 850mhz with nvidia 5200) so maybe it isn't a graphics card specific thing. 32bit CD doesn't work for my computer either  though.  :(

---

### Post by rusacarr on 2006-02-01
I have been looking into this for my machine today.  From looking through the forums, it appears that my problems are due to the drivers for my SiS video card.  There are some serious support limitations with SiS cards that I won't go into (since you have an nVidia), but if you are interested, goto [www.winischhofer.net]("http://www.winischhofer.net") for a solid description.  

I also found another couple of posts, some with screen shots, that talk about this.  Most of them relate either to unsupported hardware (my problem) or a mis-configured X server (maybe yours, may need to check your Vert and Horz refresh rates).  

There is a formal HOW-TO for NVidia drivers.  Might check it out if you have not yet. [http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")

However, I thought I saw somewhere that nVidia did have some issues with AMD64 drivers.  Not sure, though.  Since that was not my card I didn't pay much attention.

---

