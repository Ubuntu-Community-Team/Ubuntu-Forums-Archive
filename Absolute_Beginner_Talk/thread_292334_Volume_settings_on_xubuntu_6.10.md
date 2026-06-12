---
title: "Volume settings on xubuntu 6.10"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-11-03
Hello, I would like some help with my volume settings. I am using xubuntu with xubuntu-desktop on a hp pavilion dv4230us Intel celeron M 910 GML chipset.

My volume works good with gxine video, streaming video, DVD playback of wma files and other things like Xvid Divx...

but my music CD's aren't being recognized when I put them into the disk drive, and when I imported my music library from my media hda1 windows partition to Rhythmbox, all of the wma files play, but they play with barely any volume and not very clear.

Also when I go to a site like Radio.Blog.com or my own web page that has a radio.blog on it, the volume at 100% is also barely audible.

Do I need to do something with my Intel Hardware like a driver support or something like I had to do with my wireless card?

Thanks,
-c.

---

### Post by kerry_s on 2006-11-03
Try opening a terminal and run > alsamixer <use the keyboard arrow keys to adjust.

---

### Post by crimesaucer on 2006-11-03
ok.

Master is 100%
Master M is 0%
headphone is 71%
headphone is blank
PCM is 58%
Line is 0%
Line jac is blank
CD is 81%


Card: Intel ICH6
Chip: Analog Devices AD1981B
View: Playback [capture all]
Item: Master


Thanks, how should I set these for quality playback

also, will this make my CD's recognizable in the disk drive?

Thanks.

---

### Post by crimesaucer on 2006-11-03
71% seems to work for all, thanks.

Any help on my disk drive and music CD's?

---

### Post by kerry_s on 2006-11-03
The cd one should cover the cd drive, are you sure you have sound hooked up from your drive? It should be the small wire out the back of the to the board.

---

### Post by crimesaucer on 2006-11-03
I fixed my laptop, thanks. I just had to select the gxine, then select CD to play the disk. I just thought it would start automatically like the DVD does by opening up a cd rom icon/window. Thanks.

---

### Post by kerry_s on 2006-11-03
Hey, i just switched over to xfce4 so i can see clearer. If you click on the picture of the speaker you get the mixer, on the bottom of the mixer you can click on hide switches and get more options

---

### Post by crimesaucer on 2006-11-03
If you're talking about Applications-->--Settings-->--Mixer Settings (the speaker icon)...

...then I get something totally different. I get a list called Sound.

It lists the Device: Default or #0: Intel ICH6

and a drop down list of "useful controls" with everything checked.

Your help with the terminal code, "alsamixer" helped, thank you.

---

### Post by kerry_s on 2006-11-03
no i mean the one on the bar, should be next to the clock. Unless it's not there by default you can add it.

---

