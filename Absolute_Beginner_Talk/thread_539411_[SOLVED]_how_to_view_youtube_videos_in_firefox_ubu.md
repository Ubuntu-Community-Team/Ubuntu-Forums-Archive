---
title: "[SOLVED] how to view youtube videos in firefox ubuntu edgy?"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by arai on 2007-08-31
how to view youtube videos in firefox ubuntu edgy?

---

### Post by jclmusic on 2007-08-31
u need the flash plugin. i reccomend automatix - [www.getautomatix.com](www.getautomatix.com). it'll download and install the flash plugin (and many other usefull things). if u prefer, u can do it by hand.

---

### Post by arai on 2007-08-31
i don't know how to install automatix. pls help me to watch youtube videos. thanks.

---

### Post by Spr0k3t on 2007-08-31
I recommend avoiding automatix. 

if you are using 64bit you have two options.

1. 32bit browser with 32bit plugin
2. 64bit browser with 32bit plugin using 64bit wrapper.

If you are using the 32bit install of Ubuntu, you can head over to Adobe.com/flashplayer and it will give you a download to run at the terminal.

For 64bit, I highly recommend using Kilz script found here: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

Gnash, an open source flash player, has just been updated and can play Youtube videos.

Before you go trompsing off with automatix or the methods I've given above... read up on the benefits and downfalls of using automatix and base your decision off that.

Links:
[http://pimpyourlinux.com/linux-feature-review/automatix-can-break-your-linux-ubuntu-install/](http://pimpyourlinux.com/linux-feature-review/automatix-can-break-your-linux-ubuntu-install/)

---

### Post by arai on 2007-08-31
i have a 32 bit pc.

i downloaded the tar.gz file. extracted it to my desktop. now i don't know how to come to the desktop in the terminal

the terminal shows me

username@username-desktop:/$

i don't know what to do now.

[COLOR="Red"]
Update[/COLOR] : I installed flash and youtube videos are playing with sound in firefox now. 

thanx jclmusic, Spr0k3t for your support.

---

### Post by Spr0k3t on 2007-08-31
find the directory where you extracted the file.  You can change the directory by using 'cd'.  To check the directory listing, you can type 'ls' (for list).  You should see a file labelled installflash (I think, doing this from memory).  From there you should type the name of the file proceeded by "./"

For instance: ```
./installflash.sh
```

You may need to procede the ./installflash.sh with "sudo"... it's been a while since I've installed flash in 32bit.

---

### Post by Spr0k3t on 2007-08-31
Quick on the draw there arai... glad it's working!

---

### Post by Wiebelhaus on 2007-08-31
> **arai said:**
> i don't know how to install automatix. pls help me to watch youtube videos. thanks.

For god sakes man , you download it and double click it , hit install. just like an .exe

---

### Post by arai on 2007-08-31
sx66gns. that would be easy. thanks for that.

---

### Post by jclmusic on 2007-08-31
> **sx66gns said:**
> For god sakes man , you download it and double click it , hit install. just like an .exe

yep. and i don't see why there's so much automatix hate here. if u don't like it don't use it, but it is the easiest way for newbies.

---

### Post by stchman on 2007-08-31
> **arai said:**
> how to view youtube videos in firefox ubuntu edgy?

From everything I have read on here don't use Automatix.

Youtube use Flash for video.  Flash 9 is what you will need.

For Ubuntu Edgy you need to make sure the backport repositories are enabled as that is where flash 9 is.  Once that is done then use this line.

sudo apt-get -y install flashplugin-nonfree

---

