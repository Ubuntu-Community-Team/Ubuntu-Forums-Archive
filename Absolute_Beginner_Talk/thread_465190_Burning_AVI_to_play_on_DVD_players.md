---
title: "Burning AVI to play on DVD players"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-06-05
Hi, I am trying to burn a series avi files to a dvd so it can be played back on my dvd player. The DVD player does not say it supports DivX or XviD or AVI. I have once before burned the ISO of 'Steal This Film!' onto a DVD and it worked great. Is it necessary to put the files into a dvd image? If so how is that done or how can I ultimatly put the avi's on the dvd so that they will playback on the dvd player?

---

### Post by darfid on 2007-06-05
yeah i was wondering about this too

cos in the uk we get prison break about  a year after america i have to download the avis off utorrent and then burn using the vso convertx

would i have problems doing this with ubuntu

---

### Post by starcraft.man on 2007-06-05
> **mevets said:**
> Hi, I am trying to burn a series avi files to a dvd so it can be played back on my dvd player. The DVD player does not say it supports DivX or XviD or AVI. I have once before burned the ISO of 'Steal This Film!' onto a DVD and it worked great. Is it necessary to put the files into a dvd image? If so how is that done or how can I ultimatly put the avi's on the dvd so that they will playback on the dvd player?

devede is a great tool for this.

```
sudo aptitude install devede
```

alternatively open up Synaptic Package Manager from System menu and search for it under the name "devede".

You can control the bit and audio rates and a few other common options from the GUI. You can then choose in the main options to either convert it to ISO (for quick burning) or disk structure which puts it into TS folders for movie players. 

Great app, have fun :).

---

### Post by xpod on 2007-06-05
I know a lot of folks have had problems with it in feisty but i use devede for converting .avi etc to play on the dvd players.It`s pretty straightforward if you get it working ok and it`s in synaptic.

---

### Post by timcredible on 2007-06-05
a standard dvd player only plays mpeg-2 files, so you need to convert them (ffmpeg is probably the best and fastest converter, but it's cli and you may have to spend a couple minutes looking at ffmpeg -h to figure out the converting).  then you have to put them in dvd format (certain directories and different filename extensions) and add a menu (dvdstyler and qdvdauthor and lives all do this), then put it into a .iso and then burn to dvd (I think some of the above named programs do this for you now).

also, i would suspect there's some nice how-tos on the net somewhere for this.

---

### Post by xpod on 2007-06-05
ignore(just something about being tooooo slow)

---

### Post by starcraft.man on 2007-06-05
> **xpod said:**
> I know a lot of folks have had problems with it in feisty but i use devede for converting .avi etc to play on the dvd players.It`s pretty straightforward if you get it working ok and it`s in synaptic.

Ya, I noticed just a few glitches with devede. For some odd reason when I made an ISO image of some movies it wouldn't burn properly, but when I took the same file and transcoded it only to disk structure, then burned separately with k3b it worked. I am not sure why that is...

It's still my favourite app for quick and easy conversions.

---

### Post by mevets on 2007-06-05
Thanks! Shoud I worry about the Video Output format (PAL/SECAM or NTSC)? My players says its NTSC, but it mentions that when talking about the Digital TV tuner, so does it really matter?

---

### Post by xl_cheese on 2007-06-05
doing this same thing in windoze I used nero.

My dvd player doesn't ready dvd+r so I had to booktype it to dvd-rom.

Before that I converted from avi do the dvd type files using VSO something or other.

---

### Post by vanadium on 2007-06-05
Regarding NTSC or PAL, just try. Many DVD players indeed play both formats, but then perhaps otheres do not. Just try it.

---

### Post by starcraft.man on 2007-06-05
> **mevets said:**
> Thanks! Shoud I worry about the Video Output format (PAL/SECAM or NTSC)? My players says its NTSC, but it mentions that when talking about the Digital TV tuner, so does it really matter?

Ummm, since you didn't list your location it depends... usually you should encode it the same as your Country's standard. I assume its NTSC like the player says.

[Link to coding by country if you want to check.]("http://en.wikipedia.org/wiki/Image:NTSC-PAL-SECAM.svg")

---

### Post by brennydoogles on 2007-06-08
> **starcraft.man said:**
> Ummm, since you didn't list your location it depends... usually you should encode it the same as your Country's standard. I assume its NTSC like the player says.

[Link to coding by country if you want to check.]("http://en.wikipedia.org/wiki/Image:NTSC-PAL-SECAM.svg")

Should my computer be able to read both?? I just encoded a DVD into PAL (even though I live in the USA), and the sound was all crazy on the DVD. Is this an ntsc-pal issue, or did it get screwed up in the process of conversion?? Any help and pointers would be great!!

---

### Post by Unterseeboot_234 on 2007-06-17
Yes, it does make a difference concerning PAL and/or NTSC which is the TV-Signal. Basically, NTSC is verticle scan lines  running at 29.97 frames per second and PAL is a little higher resolution with horizontal scan lines doing 25 frames a second. Now, we at our house have a flatscreen TV that has a computer for the electronics. That embedded circuit board can decipher the signal correctly. Not so with a universal tape player. With the tape player, if the picture plays at all, it is a jumpy picture. Crazy, but we buy the NTSC blanks at the supermarket and record them as PAL for the universal tape player. We have two PAL-size tape cassettes on our bookshelf. I haven't seen the PAL blanks in a while.

Nero was the only program I was aware of that freely converts back and forth the NTSC/PAL and Nero is commercially available now in Linux. I don't do that much video production but I would consider Nero. Nero has a trial download.

I was hoping there was a Linux answer like ffmpeg to do the conversion.

=========

I just downloaded the trial. Linux Nero 3. It only burns CD / DVD. Does a very nice job with that and installs without any probs from their .deb. But there is No Recode. No Video Capture / Edit. This trial ain't Nero 7 with all the extras like I had over on the Win box.

---

### Post by alchemyuk on 2007-06-17
It will be a lot easier to buy a new dvd player that plays avi files.

---

