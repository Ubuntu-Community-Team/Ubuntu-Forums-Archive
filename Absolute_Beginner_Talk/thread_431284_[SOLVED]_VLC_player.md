---
title: "[SOLVED] VLC player"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-02
I used VLC player in Windows and was looking forward to using it in Ubuntu as well. My problem is that MP3 doesnt play too well in VLC. They have a lot of static. I have already installed the GStreamer packages and also the Medibuntu repository hasnt helped.

I tried playing the MP3's in Movie Player (which came pre-installed with Ubuntu) and everything plays as it should !!


Why is VLC giving me problems ?

---

### Post by jfinkels on 2007-05-02
> **Inxsible said:**
> I used VLC player in Windows and was looking forward to using it in Ubuntu as well. My problem is that MP3 doesnt play too well in VLC. They have a lot of static. I have already installed the GStreamer packages and also the Medibuntu repository hasnt helped.

I tried playing the MP3's in Movie Player (which came pre-installed with Ubuntu) and everything plays as it should !!


Why is VLC giving me problems ?

Maybe you've got bad mp3s...just a possibility :)

Do they play alright in Rhythmbox?

---

### Post by Inxsible on 2007-05-02
They play well in my Vista  and they also play well in Movie Player in Ubuntu itself !!

---

### Post by jimrz on 2007-05-02
> **Inxsible said:**
> I used VLC player in Windows and was looking forward to using it in Ubuntu as well. My problem is that MP3 doesnt play too well in VLC. They have a lot of static. I have already installed the GStreamer packages and also the Medibuntu repository hasnt helped.

I tried playing the MP3's in Movie Player (which came pre-installed with Ubuntu) and everything plays as it should !!


Why is VLC giving me problems ?

no idea, just played one in vlc and got same results as with other players. you might try 1 of the light weight players like xmms or beep

---

### Post by starcraft.man on 2007-05-02
Thats very odd... I use VLC all the time. I've never had this problem. I just played two different MP3s as well as an avi in both VLC and in Totem, I didn't notice any static or appreciable difference between them. I can only surmise that something has gone wrong with your VLC install because it should play the same quality as any other player >.> 

Maybe remove it and reinstall it. If that fails, I dunno, maybe you need to install the alsa vlc plugin? might clear up your audio problem. Its labeled vlc-plugin-alsa in the repos, try that.

---

### Post by jfinkels on 2007-05-02
> **Inxsible said:**
> They play well in my Vista  and they also play well in Movie Player in Ubuntu itself !!
Okay then.

Just curious...why are you playing mp3s in Totem and VLC?

I don't know what's wrong with your VLC, sorry friend.

---

### Post by Inxsible on 2007-05-02
I know VLC can play mp3 and a whole lot of other extensions. And now that i know its not working for VLC whereas Totem works, its kinda making me mad !!
:)

---

### Post by Inxsible on 2007-05-02
> **starcraft.man said:**
> Thats very odd... I use VLC all the time. I've never had this problem. I just played two different MP3s as well as an avi in both VLC and in Totem, I didn't notice any static or appreciable difference between them. I can only surmise that something has gone wrong with your VLC install because it should play the same quality as any other player >.> 

Maybe remove it and reinstall it. If that fails, I dunno, maybe you need to install the alsa vlc plugin? might clear up your audio problem. Its labeled vlc-plugin-alsa in the repos, try that.

Installed the alsa plugin ...still didnt help !!

I also tried installing VLC by adding the repo from the videolan guys instead of using the ubuntu one. Still no go !!

Hell it makes me mad as to why it doesnt wanna play in VLC !!

---

### Post by kubel on 2007-05-12
I'm having the same problem in VLC on Ubuntu Feisty. Sounds like bad speakers or a bad MP3 (will get static on drum beats or any loud part of a file), but it's actually VLC. It also sounds like it's playing on a cassette player that is losing power (the speed will fluctuate, barely noticeable). I haven't had this problem on any other player. Kinda sad since I was looking forward to using VLC (I've used it in Windows). :( 

Athlon XP 2000+
Soyo KT333 Dragon Ultra Platinum
C-Media CM8738 onboard sound

EDIT:

I found a fix:

1) Stop playback (changing some preferences in VLC while playing can cause it to freeze).
2) Go to Settings > Preferences.
3) Click the drop arrow next to Audio.
4) Select Output modules.
5) On the lower right corner, click the advanced options checkbox.
6) Select Linux OSS audio output (ALSA is broke).
7) Click save.
8**) Restart VLC (fix won't work until VLC is restarted).

That worked for me and now VLC is playing nice and smooth without any static. Would be nice if this bug was fixed though.

---

### Post by drs305 on 2007-05-12
Thanks for the post kubel. I had the static as did the others but it would always clear up as soon as I changed the volume level with the slider. Now it works right from the start. I appreciate the tip!

---

### Post by RSingh on 2007-05-12
I always prefer to use amarok for my default mp3 player. It is much better than iTunes and WMP. Also it has more options such as inbuilt ID3 Tag editor and Equalizer.

---

### Post by eeefresh on 2007-05-13
I was having the same problem with VLC, but Kubel's fix worked!  THANKS!

---

### Post by stchman on 2007-05-18
> **Inxsible said:**
> I used VLC player in Windows and was looking forward to using it in Ubuntu as well. My problem is that MP3 doesnt play too well in VLC. They have a lot of static. I have already installed the GStreamer packages and also the Medibuntu repository hasnt helped.

I tried playing the MP3's in Movie Player (which came pre-installed with Ubuntu) and everything plays as it should !!


Why is VLC giving me problems ?

VLC rocks, it is my ALL media player.  It does DVDs, MP3, OGG, FLAC, AVI, MPG, MP4, WMV, etc.  It plays some quicktime files but with no sound.  Thankfully there are very few quicktime files I want to play.  I also like the fact that I can play region free DVDs with VLC.

I too had the static when playing mp3s in Feisty.  I fixed it by selecting my sound card instead of default in the ALSA section.  The static went away.

---

### Post by Xerampelinae on 2007-05-28
Changing the alsa output to my specific sound card, rather than "default" also solved the issue for me.  Thanks!

---

