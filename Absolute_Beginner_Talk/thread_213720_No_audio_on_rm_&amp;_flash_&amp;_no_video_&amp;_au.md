---
title: "No audio on rm &amp; flash &amp; no video &amp; audio"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-11
I have problem w/ streaming videos on firefox. On wmv it doesn't seemed to stream at all & on rm & flash the videos shows up but no audio.
I have tried to install w32 thing. Both rm & wmv show audio & video when I download them.
Btw how do I make vlc the video player on both stream & downloaded videos?
How do I get the quicktime plugin 4 vlc?

---

### Post by Kilz on 2006-07-11
> **kris2pe said:**
> I have problem w/ streaming videos on firefox. On wmv it doesn't seemed to stream at all & on rm & flash the videos shows up but no audio.
I have tried to install w32 thing. Both rm & wmv show audio & video when I download them.
Btw how do I make vlc the video player on both stream & downloaded videos?
How do I get the quicktime plugin 4 vlc?
You may be better off installing the mozilla-mplayer plugin and mplayer for quicktime.
For the flash sound it could be one of a few things. Open a terminal and enter these
```
sudo apt-get install alsa-oss
```
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```
You might need to reboot to get it to work after the commands.

---

### Post by kris2pe on 2006-07-12
I actually I tried using this procedure 
[https://help.ubuntu.com/community/FlashPlayerStandalone?highlight=%28flash%29](https://help.ubuntu.com/community/FlashPlayerStandalone?highlight=%28flash%29)
the codes that I have enter are the following:

[COLOR="Lime"]wget [http://www.ahlrates.com/players/SAFlashPlayer.exe](http://www.ahlrates.com/players/SAFlashPlayer.exe) 

Put it somewhere central on the computer. I decided to put it in /usr/win. You can substitute this directory with wherever, or leave it where it is.

sudo mkdir /usr/win
sudo mv SAFlashPlayer.exe /usr/win/ 

Now lets make a desktop icon. Right-click on your desktop and select "Create Launcher". Name it Flash Player, and in the "Command" field type

wine /usr/win/SAFlashPlayer.exe 

You can even give it an icon. I used this one:

wget [http://www.macromedia.com/shockwave/download/images/flash_rune.gif](http://www.macromedia.com/shockwave/download/images/flash_rune.gif) 

Tuck this away somewhere like /usr/share/icons

sudo mv flash_rune.gif /usr/share/icons/ [/COLOR]

And I downloaded wine & did something to it!!!
How do I undo some of it especially the wine part coz I really have no idea what happend after configuring Wine!

---

### Post by kris2pe on 2006-07-12
Reformating it & unfortunately it had the same problem. I have download both the flash on Synaptic & I also downloaded the flash made by adobe and finally I also try to use the code you gave but still doesn't seem to work. 
I'm using creative live.

---

### Post by Epperly on 2006-07-12
That's wierd because mine has sound but no video..

---

### Post by kris2pe on 2006-07-12
You probably need the flash version given by Adobe.I got mine fixed!!! But I search in the forums & on the net b4 getting the answer!!!

---

