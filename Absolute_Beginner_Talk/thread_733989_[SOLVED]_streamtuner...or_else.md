---
title: "[SOLVED] streamtuner...or else?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-03-24
hello

I can't play any radio station on streamtuner (except for the pre-selected ones). Here's what I do: I go to Stream>NewPreselection + complete the form + press on TuneIN. A little X Multimedia system appears, and I find myself staring at it. Nothing more (I tried, among others, [http://www.radiojazz.ch/radiolive.htm](http://www.radiojazz.ch/radiolive.htm) and [http://www.jazzfm.com/player/content/nowplaying.asp?room=blue](http://www.jazzfm.com/player/content/nowplaying.asp?room=blue)). 

What am I supposed to do? And if it's not my stupidity when it comes to software, is there a good alternative to streamtuner? A normal radio streamer, I'm not interested in recording, just playing. 

Thanks.

---

### Post by jan quark on 2008-03-24
I had to install xmms to use streamtuner
```

sudo apt-get install xmms
```

---

### Post by arochester on 2008-03-24
You can stream through Rythmbox Music Player or Amarok.

---

### Post by jan quark on 2008-03-24
perhaps this guide will help you too

it covers also the recording of the streamed radio

[https://help.ubuntu.com/community/HowToRecordInternetRadio?highlight=%28radio%29](https://help.ubuntu.com/community/HowToRecordInternetRadio?highlight=%28radio%29)

---

### Post by Therion on 2008-03-24
+1 for Rhythmbox.  

It ain't gonna win any beauty contests, but you gotta give credit where it's due and Rhythmbox just... plain... works.  Streams included.

---

### Post by al.adab on 2008-03-25
Thanks everyone.

I've got XMMS (that'd be the little black box that pops in if you click on TuneIn). Preselected radios (like Virgin Classic Rock) work perfectly. I tried to include at least ten radios on Streamtuner, and none worked. Every time I go Stream>NewPreselection + copy&paste the "now playing" URL I find at the website where the stream I want to play is. I click on TuneIn, the XMMS appears, and that's it. No streaming. 

Here's a little test with some of my favourite internet radios (also including Rhythmbox and Banshee): : 
a) [http://www.jazzfm.com/player/content/nowplaying.asp?room=blue](http://www.jazzfm.com/player/content/nowplaying.asp?room=blue) (Rhythmbox tells me "Couldn't start playback. You do not have a decoder installed to handle this file. You might need to install the necessary plugins." Where can I find such plugins?
b) [http://www.radiojazz.ch/radiolive.htm](http://www.radiojazz.ch/radiolive.htm) (same as above)
c) [http://streams.wgbh.org/online/play.php?xml=897.xml&template=wgbh_audio](http://streams.wgbh.org/online/play.php?xml=897.xml&template=wgbh_audio) (it works on Banshee, same message as above on Rhythmbox, Streamtuner doesn't react
d) [http://www.bbc.co.uk/mediaselector/check/worldservice/meta/tx/analysis_tue?size=au&bgc=003399&lang=en-ws&nbram=1&nbwm=1](http://www.bbc.co.uk/mediaselector/check/worldservice/meta/tx/analysis_tue?size=au&bgc=003399&lang=en-ws&nbram=1&nbwm=1) (same message as above on Rhythmbox, Banshee and Streamtuner don't react)

Any idea? Is it my feeling or it's rather complicated to listen to internet radio on Linux? I'm not interested in recording, by the way. Just listening and having all my favourite stations on one player.

---

### Post by FrankVdb on 2008-03-25
Streamtuner uses an external audio player to play streams.

Whatever you select under Preferences > Applications > Listen to a stream > [fill in your player here]  will work, provided of course the player has been installed on your system. 

Choice abounds. 

My preferred player is Exaile (comparable with Amarok but less the problems with huge music databases).

Enjoy!

---

### Post by Therion on 2008-03-25
> **FrankVdb said:**
> Streamtuner uses an external audio player to play streams.
Bingo.

I go to [Shoutcast](http://www.shoutcast.com/) to find my streams and just copy and paste the url's I want (right-click, properties, C&P from the "Tune in!" button) into a new station in Rhythmbox and call it good.

---

