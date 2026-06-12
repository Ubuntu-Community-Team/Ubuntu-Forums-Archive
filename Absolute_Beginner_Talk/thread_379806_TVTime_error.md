---
title: "TVTime error"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by arnabbiswas on 2007-03-08
Hi,

I installed TVTime through the Synaptics installer.

I had earlier installed ivtv drivers successfully and verified the install by doing:
cat /dev/video0 > /tmp/test_capture.mpg
and playing back the capture doing:
mplayer /tmp/test_capture.mpg

However when I launch TVTime from the menu I get the following error on the TVTime window:

ivtv: Invalid argument
Cannot open capture devide /dev/video0

On running ivtv from the terminal console I get the following error:

videoinput: Card failed to allocate capture buffers: Invalid argument

Any clue please?

Thanks

---

### Post by fenian on 2007-03-09
TVTime doesnt work with ivtv.You can use mplayer to view the video from the tuner card but you have to set the channel from the command line.Open two terminal windows and in the first one type...

> mplayer -vo xv /dev/video0

In the second one type(replace # with the channel you want o view)
> 
ivtv-tune -c # -d /dev/video0

You may also want to look into [mythtv]("https://help.ubuntu.com/community/MythTV")

---

### Post by arnabbiswas on 2007-03-09
Darn! Too bad that TVTime doesnt support ivtv.

Actually I am in the process of installing mythtv and it is turning out to be quite an ordeal and a time consuming task. And since I have my ubuntu box connected to my main TV, this also means that I am not able to watch any TV and I am getting a lot of greif from my wife for that. 

So I wanted to have TVTime setup so that she could at least watch TV while I got mythtv setup. Being totally computer agnostic, the simple commands you mentioned above would be too much for her to handle. Her competence is only upto the level of moving the mouse and double clicking on icons. :) 

So is there any other TV viewer app that is compatible with ivtv? 
I would be quite surprised if there are no TV apps that support the almost ubiquitous WinTV cards.

Thanks

---

### Post by easyease on 2007-03-09
kaffeine-xine from the repo's is the simplest way to watch tv cards because mythtv is a pain in the butt to set up.

---

### Post by arnabbiswas on 2007-03-09
Splendid. 

Actually I have a WinTV 500, which is a dual tuner TV card and I have different sources connected to each tuner. So would kaffeine-xine also allow me to choose the tuner that I want to tune to?

Also, one of the sources is the Wall outlet, so would kaffeine-xine allow me to change channels on this source? 

The other source is a cable set top box and I beleive that I would need an external channel changer like an ir-blaster to change channels on. Which, I anticipate, will be a whole new adventure to set up.

---

### Post by panch0 on 2007-03-09
Not sure about Kaffeine, but in KPlayer you should be able to set up both tuners as separate DVB devices and select channel lists for each one them separately.

---

### Post by arnabbiswas on 2007-03-09
> **easyease said:**
> kaffeine-xine from the repo's is the simplest way to watch tv cards because mythtv is a pain in the butt to set up.

It seems kaffeine also does not like ivtv. I installed kaffeine-xine but it only has options for tuning DVB. This is not what I needed.

---

