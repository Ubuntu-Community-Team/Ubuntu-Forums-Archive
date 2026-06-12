---
title: "[SOLVED] How to play radio in Gutsy?"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-02-25
Hi, I'm trying to get online radio working in Gutsy, having looked at a million (okay, not quite!) methods and listened to myriad advice: I'm now completely confused. I have Totem movie player, Rhythmbox and gxine. I don't know what else I need to do, or get, or whether I should go with a different media player, making it easier to use the radio. Your help and advice is appreciated: thanks.

PS I've initially posted in Multimedia and Video but realise I was in the wrong place.  I now don't know how to move the thread so have reposted here.  Can I move the thread personally, or do I have to ask an administrator?
__________________

---

### Post by lila on 2008-02-25
Thanks for posting this thread!
I won't be of any help to you, but I was wondering the same thing, just hadn't got round to dealing with it... will follow with interest!
Lila:)

---

### Post by Duck2006 on 2008-02-25
When i had gstream on i listen to radio with xmms, not sure what they use now.

---

### Post by fenian on 2008-02-25
Install the mplayer plugin for firefox and you should be able to listen to online radio through firefox,to install open a terminal and enter...

> sudo apt-get install mozilla-mplayer

you can also use mplayer from the command line (terminal) to tune into radio streams,to do this open a terminal and type...

> mplayer + the url for the stream for instance to listen to BBC 5 you would type...
mplayer [http://www.bbc.co.uk/fivelive/live/surestream_int.ram](http://www.bbc.co.uk/fivelive/live/surestream_int.ram)

---

### Post by trigun on 2008-02-25
rhythmbox supports that....

---

### Post by guilly on 2008-02-25
Ya I second rythmbox, It's great, just copy the URL from the website and it'll save it. Once you have it saved into rythmbox you don't have to worry abotu browsing to your favorit radio station every time.

---

### Post by wolfen69 on 2008-02-25
try streamtuner. it has shoutcast and a few other online radio services built in.. you will also need to download xmms player to use it. both are available in synaptic.

btw, streamtuner is way better than rhythmbox for streaming radio. everything is built in.

---

### Post by Therion on 2008-02-25
1.  Go to [Shoutcast](http://www.shoutcast.com/).
2.  Right-click on the "Tune in!" button and copy the URL location.
3.  Open Rhythmbox, click on right-click on Radio and paste in URL from step 2.
4.  Right-click on the URL in the Radio section of Rhythmbox and enter the info for the properties (genre, etc.) so it looks good.
5.  Profit!  Wait... What??

> **wolfen69 said:**
> btw, streamtuner is way better than rhythmbox for streaming radio. everything is built in.
Poor Rhythmbox... It's like the ugly girl at school you don't want to be seen around, but have a totally *awesome* time with when you go out (secretly).

---

### Post by RedRat on 2008-02-25
First make sure that you have xmms and/or audacity installed. Then you might want to use these two front ends: streamtuner and tunapie. Another possibility is to install Amarok. Both Streamtuner, tunapie, and Amoarok allow you to tune into Shoutcast broadcasts (they are the Winamp people). 

You will need some codecs also. Please check this thread out:

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

It may appear long and complex but it pretty much takes you through all you will need for streaming radio. Do not be afraid, but you will have to use the command line for some of it. But this is a very helpful thread.

---

### Post by ubuntu-freak on 2008-02-25
Thanks for recommending my thread RedRat.
 
Audacious is a sweet Winamp-style player, although the MPlayer plugin works fine for radio, as does RealPlayer's plugin for RM formats. XMMS is dead now right? That's why I recommend Audacious, looks nice too. 
 
My how-to shouldn't scare anyone, I hope. Basically it's a cut 'n' paste job, a great advert for the command line, simple and quick! 
 
Nathan
 
P.S. I've never needed Xine. Some tell new users to install it for DVD playback, but VLC is best for that anyway. Others recommend it for streaming (xine-plugin), but mozilla-mplayer has always served me well. GStreamer (default Totem) is good for some weird vids that don't play in MPlayer, and vice versa. GStreamer is removed if you install totem-xine.

---

