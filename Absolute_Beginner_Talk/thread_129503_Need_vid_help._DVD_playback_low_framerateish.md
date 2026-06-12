---
title: "Need vid help. DVD playback low framerateish"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by gordong11 on 2006-02-13
Hello

I'm running Ubuntu 64 bit Breezy on an MSI Mobo with ATI graphics set to VESA and 128mb of ram and my DVD playack is sluggish, not watchable. It bogs down my machine to the point my mouse barely moves.

I finally got my playback to work, only Gxine works for me, and is cool...but this issue is killing me. I have tried to activate DMA transfer, as shown by Wiki, but it either is not woeking, or I"m doing something wrong beacsue when in terminal:

sudo hdparm /dev/hdc
I get a No file error

even after doing steps 2 through 4 on wiki page [https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)  . I still get no file found. Any ideas? Possibly somehting dofferent 64bit?

Also is VESA the best I can do? is there an alternative that is possibly better? lastly, would changing mt resolution for the desktop to 800X600 help at all?

Thanks

---

### Post by Jedeye on 2006-02-13
have you tried Automatix to install the dvd codec? I am new, so I dont have many solutions... thats what just worked for me... run a search for Automatix if you have never used it... its great.

---

### Post by gordong11 on 2006-02-13
[QUOTE=Jedeye]have you tried Automatix to install the dvd codec? I am new, so I dont have many solutions... thats what just worked for me... run a search for Automatix if you have never used it... its great.[/QUOTE]

I'm actually trying to play Mpeg-2 DVD's, and not store bought..so I shouldnt need codecs. Anyway, they play, but horribly SLOOOW. ITs kind of like 1 seond play well, 2 seconds of catching up, then all over again.

Store bought DVD's is a whole nother thing. Even internet AVI's and Mpegs play the same on my machine. but thanks

---

### Post by steevc on 2006-02-16
I found that 

hdparm /dev/hdc

does not work, but 

hdparm /dev/cdrom does. My DMA was off and turning it on made DVD playback much smoother.

I'm just going to try adding something to my /etc/hdparm.conf to make this permanent.

EDIT: Just realised the DVD drive is hdb, not hdc. You live and learn.

---

