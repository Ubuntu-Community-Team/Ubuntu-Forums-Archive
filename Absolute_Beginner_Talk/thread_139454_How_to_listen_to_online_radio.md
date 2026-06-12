---
title: "How to listen to online radio?"
date: 2006-03-04
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2006-03-04
I have already Rhythmbox installed and I would like to listen to some online Radio. Is it possible for example this one: [http://sky.fm/](http://sky.fm/)
They have 3 sound types, which one will run on Ubuntu 5.10? Do I have to install additonal codec?

---

### Post by Zimmer on 2006-03-04
Well, I was curious , so I just did this.
Opened the feed link to the particular station on the site and cancelled the opening/downloading of the 'file'.
Copied the URL from the address bar and pasted it into the dialog box for new radio station in Rhythmbox.. Voila! it works....I do have the gstreamer0.8 codecs loaded..

---

### Post by Zdravko on 2006-03-04
hmm, it appears that I have this codec also installed. But none of the formats works for me :(

---

### Post by Zimmer on 2006-03-04
[QUOTE=Zdravko]hmm, it appears that I have this codec also installed. But none of the formats works for me :([/QUOTE]
I have MP3 codec and am using the Winamp stream.
Many thanks for the link, BTW :)

EDIT:  are you getting any error messages? or just an exclamation mark in front of the station ID?
AND this link may help you with the LAME codec
[http://www-users.york.ac.uk/~raa110/audacity/AudacityHelp.html#LAME](http://www-users.york.ac.uk/~raa110/audacity/AudacityHelp.html#LAME)
or try Easy Ubuntu to set up the missing codecs.

---

### Post by Zdravko on 2006-03-04
No, I get "Unexpected stream input" error message and then an "!" in front of the field. This happens for every format :(

---

### Post by Zdravko on 2006-03-04
Nobody knows? Or nobody listens to online radio under Linux? Impossible...

---

### Post by darkmaze on 2006-03-04
quod libet allready has those stations listed in the stations tab might try that

---

### Post by Zdravko on 2006-03-04
What is "quod libet"?

Edit: darkmaze, I downloaded this program... It is worse than RhythmBox :(

---

### Post by lunadog on 2006-03-04
You can check out my program Tunapie: 

[http://www.sourceforge.net/programs/tunapie](http://www.sourceforge.net/programs/tunapie)

to get the shoutcast listings of radio and tv streams under Linux.

Then use xmms or beep-media-player to play the audio streams and mplayer or xine to play video nsv streams. I have never had a problem with playing audio streams, but video streams can be a bit more problematic.

James

---

### Post by BoyOfDestiny on 2006-03-04
Yeah, streaming audio works in Linux. In fact, that is the first thing I ever tried in Linux (on a knoppix live cd 2 years ago or so...) :)

---

### Post by RaiSuli on 2006-03-04
I listen to internet radio a lot, normally with either xmms or vlc player. If you use  Firefox as a browser, make sure you have installed an extension called "media player connectivity". It comes with its own wizard and lets you choose players for audio and video streams. That worked for me.

---

### Post by Zdravko on 2006-03-04
Finally it worked... I installed a couple of other apps, and maybe some other dependencies. Now RhythmBox plays online radio! Great! But I would like to see the web page for each song. In sky.fm for every song there is a thread in the forum. In Windows under Media Player 10 I could post my comments straight in the player - very convinient. Is there some option for this here?

---

### Post by lunadog on 2006-03-04
Streamtuner has a button to go to the home page associated with the stream, but I don't know of any program that links directly to forum comments.

James

---

### Post by Zdravko on 2006-07-27
Whoops. Now I have Dapper, and it seems that Rhythmbx cannot play radios from sky.fm anymore. Can anyone suggest me a sollution? Please, it is a really great station!

---

### Post by chipper_30 on 2006-07-27
The winamp links work fine with me, using xmms.

---

### Post by Zdravko on 2006-07-27
XMMS:
I chosed Play->Play location -> [http://www.sky.fm/mp3/newage.pls](http://www.sky.fm/mp3/newage.pls)
No effect.
Then I enabled the playlist editor ->add->add url ->[http://www.sky.fm/mp3/newage.pls](http://www.sky.fm/mp3/newage.pls)
No effect.
Any idea?

---

### Post by cjm5229 on 2006-07-27
```
sudo apt-get install streamtuner
``` Streamtuner will get Shoutcast and live 365 stations.
It uses XMMS as a player.

---

### Post by chipper_30 on 2006-07-27
Yeah, I don't know why but it doesn't work for me either... This is what I do: click on the link using your browser, then save the file. Finally drag the file on xmms, or use "load playlist" (bottom right) and look for the file...
I haven't tried with newage, but tophits works that way.

---

### Post by Zdravko on 2006-07-27
Oh, I finally got it to work. I saved the pls file. Then I dragged it over the playlist in xmms. Now the strangest thing is that 4 pieces appear - why? It seems that 3 of them work and play the same - my beloved New age station.

---

### Post by chipper_30 on 2006-07-27
I have that with many radios, I think it's because there are more than one server broadcasting. In case one of them is saturated or off, you can just use an other one.

---

