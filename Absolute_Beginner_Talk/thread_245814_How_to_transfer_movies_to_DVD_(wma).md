---
title: "How to transfer movies to DVD (wma)?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Corvair on 2006-08-28
I am trying to burn video cds and video dvds so I can watch them on TV with my DVD reader. I downloaded films in avi format and when I try burning I get avi format again. How do I burn in wma format so I can wath on tv? Which program should I use.I thought gnomebaker would do it but there is only data and audio, no video choice.

---

### Post by kidders on 2006-09-04
To my knowledge, WMAs won't play on a DVD player ... you probably want to use the DVD video format. I'd use mencoder (part of mplayer) for this.

---

### Post by Marsolin on 2006-09-04
You'll need to use the DVD format instead of WMA unless you want to hook a computer up to your TV. [K9Copy]("http://linuxappfinder.com/package/k9copy"), [K3b]("http://linuxappfinder.com/package/k3b"), and [xDVDShrink]("http://linuxappfinder.com/package/xdvdshrink") are a few options. I talk about them both in [this article]("http://linuxappfinder.com/dvd_rippers1.php").

---

### Post by taurus on 2006-09-04
If you have a movie in avi, use DeVeDe to convert it to DVD...

---

### Post by Corvair on 2006-09-04
Thank you all for your reply. 
What I want to do is to be able to transfer the movies to a viewable format on my Panasonic DVD player and watch them on my TV. On my Panasonic it says WMA/MP3/JPEG  DVD-RAM VIDEO PLAYBACK.
I will try what you are suggesting.

Also, I have transferred some music to DVD. I can listen to it on my Panasonic reader but not on my older Denon player, Why? I can alsi listen to it on my cd alarm clock.

Thanks again

---

### Post by taurus on 2006-09-04
The best way to go is to use DeVeDe to convert it to a DVD format and burn it to your DVD.  Then, you can play it on any standalone DVD player.  No need to convert it to something else first and then burn it...  That's probably the easiest way to go.

---

### Post by Corvair on 2006-09-04
I have downloaded devede23 from rastersoft.com since I can't see it i  synoptic. I am trying to install it using  <sudo apt-get install devede23> on a terminal but it tells me that it can't find it. I have it in tmp-file.
Can you tell me how to install it? I have installed everything else that I need to run it

---

### Post by taurus on 2006-09-04
You can't install devede like that!!!  You first must unzip it and then run the installer.  Open a terminal, Applications -> Accessories -> Terminal, and type

```

cd ~/Desktop (assuming you have downloaded it to your ~/Desktop directory...)
tar xvjf devede23.tar.bz2
cd devede23
sudo ./install.sh

```
It should be in Applications -> Sound & Video -> DeVeDe now.  Otherwise, just type "devede" from the prompt to run it...

---

### Post by Corvair on 2006-09-04
devede23 is now installed and looks good.
Thanks to everyone for the help and information. 

I also downloaded K3B which should be good to make music cds.

Thanks to the great Ubuntu community.

---

### Post by taurus on 2006-09-04
If you are using devede to convert your avi to DVD, I recommand you pick the iso option.  If you have a 700MB file with a decent speed, it shouldn't take more than 1 hour and the file is in .iso format.  Then, use k3b to burn it as an image file.  Another 15 minutes and just pop that sucker into a standalone DVD player and you can watch your movie on your big screen tv...  ;)

---

### Post by halitech on 2006-09-04
I like doing things by CLI so if you  want to try that, follow the info here:

[http://smorgasbord.net/convert_video_linux]("http://smorgasbord.net/convert_video_linux")

---

