---
title: "How can I listen to Winamp Shoutcast stations?"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-11-30
Hi I'm used to listen to Winamp Shoutcast radio stations whenever I use Windows.  But how do I do that in Ubuntu plus some stations use this abacast software which complicates thing doubly!
lets say I want to listen to these what will I have to do?
[http://www.streamingsoundtracks.com/](http://www.streamingsoundtracks.com/)
[http://filmmusicworld.com/radio/index.php?](http://filmmusicworld.com/radio/index.php?)

I would appreciate complete step by step directions from beginning to the end tnx.

---

### Post by bodhi.zazen on 2006-11-30
Try [songbird](http://doc.gwos.org/index.php/SongBird)

You will have to wait a minute or two....

The servers are down, but check it out later today....

---

### Post by ninjaPants on 2006-11-30
You'll need to install streamtuner (at least).
[Project homepage]("http://www.nongnu.org/streamtuner/")
You can install it by typing in a terminal
```
sudo apt-get install streamtuner
```
say yes to install dependencies you may not have.
or you can install automatix (automatix2 if you're on edgy) and choose to install streamtuner and a bunch of other stuff. [link - website's down at time of this post]("http://www.getautomatix.com/")
By default, streamtuner uses xmms to open streams. You can change these settings in edit>preferences or if you want xmms, install it from synaptic or apt-get. 
Songbird (linked above) is also an option, but it's still in early alpha, so it can be unstable. Here's a link to and installation script/instructions -[click]("http://www.psychocats.net/ubuntu/songbird"). After you install it, run it by pressing alt+f2 and typing Songbird (case specific) You can add an application launcher to the menu or top panel if you want - search the forums for instructions on that. 

Hope this helps

---

### Post by thegino on 2006-11-30
> **ninjaPants said:**
> You'll need to install streamtuner (at least).
[Project homepage]("http://www.nongnu.org/streamtuner/")
You can install it by typing in a terminal
```
sudo apt-get install streamtuner
```

Now thats one awesome radio tuner for shoutcast, way better then Tunapie

One thing missing is TV streams :( 

Any good free tv streamers out there too...

---

### Post by arnieboy on 2006-11-30
> **ninjaPants said:**
> (automatix2 if you're on edgy)
FYI: also if you are on Dapper.

---

### Post by CarpKing on 2006-12-01
VLC (sudo apt-get install vlc) does streams pretty well.  Once installed, go to File--> Open Network Stream.  On the first website you posted (the second says its stream is down), right click on one of the streams under "Listen" on the left side and click "Copy Link Location."  Now go back to VLC, click HTTP, and paste into the URL field.  Then hit open.  

Actually, the same can be accomplished in Totem (the default movie/music player) with Movie--> Open Location.  Then just paste the URL like before.  Totem only worked with the Winamp stream and the Ogg stream on that page, while VLC worked with all four.  But since all the streams are the same, use whichever you like.  The Ogg stream probably works in the default player on a fresh install of Ubuntu, without any messing around with codecs.  Most streams aren't that friendly.  

If you do "Copy Link Location" on the second page you posted, you'll have to sort the URL out from a bunch of other code.  You'll want the URL that ends with .pls.  

Both VLC and Totem should in theory be able to do video streams as well.

EDIT:  I just remembered that I have the Xine backend for Totem.  The default is the Gstreamer backend.  I don't know if that affects anything, but don't be surprised if your Totem doesn't work quite the same as I described.

---

### Post by jingo811 on 2006-12-01
OK you ppl are going a little bit too fast for me :neutral: hold your horses!
After having installed streamtuner I click on
[http://www.streamingsoundtracks.com/](http://www.streamingsoundtracks.com/)
and choose to open winamp stream with streamtuner when the popup box appears, but nothing much happens after it's launched.  But in Streamtuner when I do a search I find the streams.  But when I play them XMMS starts and loop its pre-buffering sequence again and again.  No sound!

What am I doing wrong? (this is regarding the winamp stream)
When clicking the ogg stream the embedded mplayer starts without hassle, but I want to learn how to access the winamp stream.

---

### Post by KuriKai on 2006-12-01
I guess you need an mp3 codec. someone will come along and tell you how to install it.

---

