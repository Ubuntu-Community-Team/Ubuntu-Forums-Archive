---
title: "Theme and Mplayer help requried"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by maxim1 on 2007-04-08
I nearly have finished setting up Ubuntu on my laptop so far I love it just a couple of issue to resolve and i will be completely happy.   


can any one tell me what theme is being used in this youtube video 

[http://www.youtube.com/watch?v=i0ZtcxHUSDQ&mode=related&search=](http://www.youtube.com/watch?v=i0ZtcxHUSDQ&mode=related&search=)


I know beryl is being used but i would like to know are the icons just short cuts or part of a  theme 

also does any one know if any configuration needs to be down in M player, i get this error message could not open/initialize audio device > no sound 

the other media player works fine but I would prefer to use M player.

---

### Post by overdrank on 2007-04-08
> **maxim1 said:**
> I nearly have finished setting up Ubuntu on my laptop so far I love it just a couple of issue to resolve and i will be completely happy.   


can any one tell me what theme is being used in this youtube video 

[http://www.youtube.com/watch?v=i0ZtcxHUSDQ&mode=related&search=](http://www.youtube.com/watch?v=i0ZtcxHUSDQ&mode=related&search=)


I know beryl is being used but i would like to know are the icons just short cuts or part of a  theme 

also does any one know if any configuration needs to be down in M player, i get this error message could not open/initialize audio device > no sound 

the other media player works fine but I would prefer to use M player.


Hi the theme looks like either KDE or the Xcfe ( I think that is what it is called)
I think you are needing the codecs for the player. i use automatix to install the codecs needed to play video. Hope this helps and welcome, good luck!:)

---

### Post by maxim1 on 2007-04-08
I used easyubuntu  to install mplayer and codecs

---

### Post by RomeReactor on 2007-04-08
Hi. Open Mplayer and right-click on the screen and select "Preferences-->Codecs & demuxer" and for the **Video codec family** choose either **Null video decoder** or **FFmpeg's libavcodec codec family**; for the **Audio codec family** choose **FFmpeg/libavcodec audio decoders**. The w32codecs aren't really needed unless you want to view .wmv files.

Also, if you have an Audigy soundcard, further configuration may be needed.

---

### Post by maxim1 on 2007-04-09
sorry did not help, here is my audio card thingy 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

Im not sure what make the sound card is as its an integrated laptop one the laptop is a ASUS G1 model

---

### Post by RomeReactor on 2007-04-09
When you open Preferences in Mplayer, on the first tab (Audio), is ALSA selected?

---

### Post by maxim1 on 2007-04-10
No oss is selected

---

### Post by maxim1 on 2007-04-10
Selected alsa, now working fine nice one mate :guitar:

---

