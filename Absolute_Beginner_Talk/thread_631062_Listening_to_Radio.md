---
title: "Listening to Radio"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Dumpy Dumpster on 2007-12-04
How can one listen to the radio with Ububtu?

---

### Post by smacattack on 2007-12-04
Depends if you want to listen to local radio or stations broadcast online.

If the station(s) you want are online you should be able to listen through your browser, or if there is an .asx file that they provide, you can add it to the 'Radio' section in Rhythmbox and stream it from there whenever you want (or Totem or many other programs if you prefer). I listen to a bunch of radio stations online that way (like cbcradio or radio netherlands).

For local radio I believe you need a radio tuner but I'll hand that off to someone else...

---

### Post by Dumpy Dumpster on 2007-12-04
Sorry my question lacked some substance!   I was typing in the question to first see if any other similar threads came up in search - they didn't and I pressed a wrong key!!
I was wanting to listen to BBC and was told that due to dial-up, I needed Windows Media Player.  I shouldn't think there is a hope in hell of Win. Med. Player working on Ubuntu, so I was wondering if there was an alternative.
Anyway thanks for your reply.

---

### Post by jken146 on 2007-12-04
Yeah, you can use Rhythmbox if you like.  VLC will probably work too for almost anything.  You'll need the right codecs, but that depends on what kind of stream you want to play.

---

### Post by Dumpy Dumpster on 2007-12-04
> **jken146 said:**
> Yeah, you can use Rhythmbox if you like.  VLC will probably work too for almost anything.  You'll need the right codecs, but that depends on what kind of stream you want to play.  

Thank you jken146, but what on earth is a codecs, how do I find out what I need and where are they located?  Absolute Beginner in the Absolute Beginners Forum!!!

---

### Post by SpacePilot on 2007-12-04
VLC will have any codec you need.

---

### Post by fenian on 2007-12-04
To listen to BBC Radio use mplayer,to install the necessary packages open a terminal and type...> 

sudo apt-get install mplayer mozilla-mplayer

You can then listen to radio streams from the command line (terminal window),by typing...

For BBC 1
> 
mplayer -playlist [http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram](http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram)

For Radio 2

> mplayer -playlist [http://www.bbc.co.uk/radio2/realmedia/fmg2.ram](http://www.bbc.co.uk/radio2/realmedia/fmg2.ram)

For Radio 3
> 
mplayer -playlist [http://www.bbc.co.uk/radio3/ram/r3g2.ram](http://www.bbc.co.uk/radio3/ram/r3g2.ram)

For Radio 4
> 
mplayer -playlist [http://www.bbc.co.uk/radio4/realplayer/media/fmg2.ram](http://www.bbc.co.uk/radio4/realplayer/media/fmg2.ram)

For Raadio 5

> mplayer -playlist [http://www.bbc.co.uk/fivelive/live/surestream_int.ram](http://www.bbc.co.uk/fivelive/live/surestream_int.ram)

For World Service 

> mplayer -playlist [http://www.bbc.co.uk/worldservice/meta/tx/nb/live_news_au_nb.ram](http://www.bbc.co.uk/worldservice/meta/tx/nb/live_news_au_nb.ram)

For info on installing codecs to play more media formats look [here.]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Dumpy Dumpster on 2007-12-05
Many,many thanks fenian.  Just what the doctor ordered.  All downloaded and working.
Thanks also SpacePilot for your help.

---

### Post by mamadu bwana on 2008-04-03
Fenian,

A big 'thank you!!' for this.  I love listening to the radio via the CLI.  You really made my day!

---

