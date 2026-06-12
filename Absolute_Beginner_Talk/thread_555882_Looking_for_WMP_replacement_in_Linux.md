---
title: "Looking for WMP replacement in Linux"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by T3KN33K on 2007-09-20
Hello!  

I've been interested in Linux for sometime now, and I finally decided to devote a portion of my hard drive to experimenting with Ubuntu.  I am a long time and knowledgeable Windows user, and as such, am obviously not quite willing to entirely do away with it yet.  My system is now dual booting Vista (which was such a disappointment that it became the motivating factor in exploring Linux) and Ubuntu 7.04.  Since I installed Ubuntu about 2 months ago, I've been using it sparingly in my free time, while still relying on Vista for the vast majority of my functions.  I would, however, eventually like to wean my dependency off of Windows in favor of Linux, as the benefits of doing so are becoming readily apparent to me, even with my so-far limited experience.  

That said, one of the biggest things holding me back right now is my media collection... I have aprox. ~1000 full length movies, documentaries, and television series as well as ~20000 audio tracks.  To play audio, I solely use WMP 10, and for video, WMP classic embedded with the all-in-one k-lite media codec pack, which literally plays everything I've thrown at it.  

As I think we all would agree, there is a lot to be desired ATM with video, caused by an absolute mess of proprietary codecs, formats, and players.  Prior to finding the WMP classic with KLM codec pack, I primarily used VLC media player to watch my movies.  I have found the only thing missing from VLC is the ability to play Real's .rmvb format, in which I have many television series encoded.  ...Prior to VLC, I used a combination of Realplayer, Quicktime, WMP 9, etc.  This was most undesirable and annoying.

So my question is this:  Is there any suitable video player for Linux that will play .wmv, .mov, .rmvb, .avi, .mpg, etc?  Is VLC my best option?  

...Also, for an audio player...  what is there available that best satisfies these requirements:

-plays .mp3, .wma, and preferably (but not required) .mp4
-efficient and organized music management system, with unlimited playlists.
-ability to monitor multiple folder for new downloads, and import to library automatically.
-support for 20000 ~ 30000 songs

also, as far as an audio player goes, WMP 10 has made me a sucker for a nice/fancy GUI, so that would be a bonus as well.  

Thanks in advance to any responders! 

-T3KN33K :popcorn: :guitar:

---

### Post by st33med on 2007-09-20
VLC is a really good option.

---

### Post by Daveth on 2007-09-20
VLC for movies, and the most excellent Amarok for all your tunes.

---

### Post by Lord Illidan on 2007-09-20
After you've installed the restricted codecs, then most movie players should be sufficient.

Amarok can handle all those very well. The GUI is more like Itunes, I guess..

---

### Post by Joakim Stokland on 2007-09-20
Hi and welcome to the community!
I'm not quite sure about the video playback, but I've fallen quite in love with Amarok. It's a bit iTunes-alike. You can download skins, and the library is excellent. It monitors the folders you specify, and it can use the "standard" codecs in Linux. I'm not sure about which codec to use for .wma though, but it is intelligent enough to let you know what codec it needs when you try to play a file.
Hope this gives you a start.
Good luck!
Joakim

---

### Post by Matakoo on 2007-09-20
> **T3KN33K said:**
> 

So my question is this:  Is there any suitable video player for Linux that will play .wmv, .mov, .rmvb, .avi, .mpg, etc?  Is VLC my best option?  

I don't know about .rmvb (I'm allergic to Real and their formats and am doing my best to stay clear of those as far as possible - which is quite easy nowadays), but VLC handles the rest just fine. That being said, I would install another player and the w32codecs as well (or the w64codecs if you run 64-bit). The codecs can, if you don't have them already, be installed easily if you follow the instructions at medibuntu.org. Why another? Well, maybe it's just me but I have some files that VLC isn't quite happy with. They play, but other players sometimes do it better. I personally would suggest Kaffeine.

> **T3KN33K said:**
>  ...Also, for an audio player...  what is there available that best satisfies these requirements:

 -plays .mp3, .wma, and preferably (but not required) .mp4
-efficient and organized music management system, with unlimited playlists.
-ability to monitor multiple folder for new downloads, and import to library automatically.
-support for 20000 ~ 30000 songs

also, as far as an audio player goes, WMP 10 has made me a sucker for a nice/fancy GUI, so that would be a bonus as well.  

Thanks in advance to any responders! 

Here Amarok is your friend. The best audio-player for any platform, period. It leaves WMP. WinAMP, and iTunes far, far behind.

---

### Post by T3KN33K on 2007-09-20
Thank you all very much for your responses, it seems like a sweeping victory for Amorak!

---

### Post by SonicSteve on 2007-09-20
I have a mutt Ubuntu install,
I install Ubuntu then download the KDE desktop.
This gives me Gnome along with much of KDE.
KDE uses a media player called Kaffeine, it's quite polished. Amarok for audio is the best I've found, I wish there was  a windows version.

If you're new to Ubuntu and Linux this site [www.psychocats.net](www.psychocats.net) is a great resource.

---

### Post by twickline on 2007-09-26
Well, I have put a Windows Media Player 9 & 10 howto on my blog if your interested in running the player in wine.

[http://wine-review.blogspot.com/2007/09/windows-media-player-9-10-on-linux-with.html]("http://wine-review.blogspot.com/2007/09/windows-media-player-9-10-on-linux-with.html")

---

### Post by Lord Illidan on 2007-09-26
Interesting, but not my cup of coffee..

---

### Post by SonicSteve on 2007-09-30
> **twickline said:**
> Well, I have put a Windows Media Player 9 & 10 howto on my blog if your interested in running the player in wine.

[http://wine-review.blogspot.com/2007/09/windows-media-player-9-10-on-linux-with.html]("http://wine-review.blogspot.com/2007/09/windows-media-player-9-10-on-linux-with.html")

Interesting,
does it run with strange flicker, or choppyness? I ran IE in wine just to try it once and I found it flickery and buggy.

---

