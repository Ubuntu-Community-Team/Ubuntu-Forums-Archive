---
title: "Play DVDs"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by grebarton on 2008-01-17
I can't play any DVDs in Gutsy.

I have installed win codecs, and followed loads of guides such as [https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd)

I have tried GXine, Totem, Ogle and pretty much any other DVD player.

Anyone got any ideas because it seems like this should be something easily available?

---

### Post by zipperback on 2008-01-17
> **grebarton said:**
> I can't play any DVDs in Gutsy.

I have installed win codecs, and followed loads of guides such as [https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd)

I have tried GXine, Totem, Ogle and pretty much any other DVD player.

Anyone got any ideas because it seems like this should be something easily available?


[http://getautomatix.com/](http://getautomatix.com/)

- zipperback
:popcorn:

---

### Post by PeterJS on 2008-01-17
Installing DVDcss from medibuntu is usually easier.
Full details:
[http://medibuntu.org/](http://medibuntu.org/)
DVDcss debs:
i386:
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
x64:
[http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)

---

### Post by crjackson on 2008-01-17
> **grebarton said:**
> I can't play any DVDs in Gutsy.

I have installed win codecs, and followed loads of guides such as [https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/7.10/musicvideophotos/C/video.html#video-dvd)

I have tried GXine, Totem, Ogle and pretty much any other DVD player.

Anyone got any ideas because it seems like this should be something easily available?

 Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and past the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

You probably won't have any trouble after this.

---

### Post by bob12564 on 2008-01-17
I had a similar problem and tried your procedure.  I can now view Real streams and all of my movie clips.  However, I still don't have full DVD playback.

If I insert a commercial DVD, Totem Movie Player opens and the movie plays normally. But MPlayer and Xine Movie Player don't seem to be able to see the disk.

If I try to play a DVD-R, none of the players recognize the disk as a DVD.  They seem to be treating it as a data disk not a playable DVD.

So...things are better but not great.  From what I can see on the beginners' forum, DVD playback seems to be elusive for most of us.  Everyone seems to have their favorite movie player software but I think this is more fundamental than which player to use.  Totem, Xine, MPlayer, VLC, etc. all have DVD playback capability of some sort.  A DVD disk should be recognized in all of them.  It's frustrating.

---

### Post by PeterJS on 2008-01-17
What it ultamately comes down to is that decoding DVDs under linux in the US is illegal, so rather than each project tightly integrating a dvd decoder so they all work well, the offer just enough supprt of libdvdcss, that thing usually work, but if push comes to shove and they end up in court, it's not their fault blame the frenchmen at VLC. VLC is obviously different, as it's by the same authors of libdvdcss, so it tends to work the best with it. Yes DVDs should work well in all players but given the current legal standing of doing so everyone nobody wants to be the one the write the dvd decoder.

---

### Post by bob12564 on 2008-01-18
Peter,

Thanks for clarifying that.  I had no idea there were legal issues in the U.S.  For those of us accustomed to Windows, playing a DVD simply means having a DVD codec installed.  Once it's there, a DVD will play in Real Player, Windows Media Player, PowerDVD, etc.  I can now understand that the folks supporting MPlayer, Totem, etc. are dancing around the issue to avoid lawsuits.

While the Ubuntu forums are great and very helpful, I find many of the responses to be way over the heads of newbies.  I've asked questions before but many well-meaning posters end up in their own side conversation debating one software package over another leaving instead of answering the question that was originally asked.  I think many newbies get frustrated as a result and head back to Windows.  Those of us new to Linux are really trying to learn the concepts first and foremost.    So, once again, thanks for explaining the concept!  

I'll try VLC and see what happens.  If VLS works, should I dump Xine, MPlayer, and Totem?  BTW, is there a common codecs directory that all these products use like there is in Windows.  I ask this because GStreamer seems to load its own while Mplayer has its own set, etc.  I don't want to uninstall a player and end up losing the codecs too.

Thanks for the help.

---

### Post by PeterJS on 2008-01-18
> **bob12564 said:**
> Peter,

Thanks for clarifying that.  I had no idea there were legal issues in the U.S.  For those of us accustomed to Windows, playing a DVD simply means having a DVD codec installed.  Once it's there, a DVD will play in Real Player, Windows Media Player, PowerDVD, etc.  I can now understand that the folks supporting MPlayer, Totem, etc. are dancing around the issue to avoid lawsuits.

It's catch 22, all the people licensed sell DVD decoders only make them for Windows, and all the people that make Linux DVD decoders aren't licensed to sell them. So the only decoder you can buy won't work, and the only decoder you can get isn't legally sanctioned and therefor illegal under the DCMA.


> 
I'll try VLC and see what happens.  If VLS works, should I dump Xine, MPlayer, and Totem?  BTW, is there a common codecs directory that all these products use like there is in Windows.  I ask this because GStreamer seems to load its own while Mplayer has its own set, etc.  I don't want to uninstall a player and end up losing the codecs too.

Thanks for the help.

Kinda... There are two big plugin engines gstreamer and xine. So a media player that works with gstreamer will be able to use all the gstreamer codecs, and one that works with xine will use all the xine codecs. And then there are some media players that themselves have plugins that allow them to use either xine or gstreamer codecs. Generally these plugins conflict with one another, so you can only have one installed at a time, so an app will be tied to a specific codec set. I've never bothered with individual codecs, but instead used the *buntu-restricted-extras package that corresponds to the Desktop Environment I'm using most.

As for VLC, it's an entirely different beast, there are no plugins for VLC. VLC includes almost everything, and what it doesn't include it has installed as required dependencies (ffmpeg, etc), and interacts with directly.

EDIT: glossed over the mention of MPlayer, no idea how it works.

---

### Post by nikoPSK on 2008-01-18
> **zipperback said:**
> [http://getautomatix.com/](http://getautomatix.com/)

- zipperback
:popcorn:

Automatix is bad, please don't use it. It has been known to break installs.

> **crjackson said:**
> Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Gutsy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and past the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
``````
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
``````
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```You probably won't have any trouble after this.

thank you for saving me the time of writing this. :P

---

### Post by bob12564 on 2008-01-20
Peter,

Thanks for the additional information.

I installed VLC and I now have DVD playback with some anomalies.  Previously, I had DVD playback via Totem and Xine with commercial DVDs.  DVD-Rs that I burned with my Panasonic DMR-HS2 table-top burner were only recognized as data disks.  I can now play them but only via VLC.  I also noticed that they have some strange quirks in VLC.  For one thing, playback stalls for a split second every 30 seconds or so.  Also when I look at the disk menu, all VLC shows is the first title.  However, if i move my mouse cursor over the menu, the other titles appear but only as long as I pause the cursor over the menu slot where it should be appearing.  I'm now thinking that there's something unusual about the way the Panasonic is burning the DVD-Rs, although they are trouble free in all DVD players and they play fine under Windows.  I can live with it but I'm curious about it.

On the issue of codecs, I noticed that I could not play Indeo 5 encoded movie clips via VLC.  Beforehand I had downloaded MPlayer and its non-free codec package because support for Indeo 5, Real Player, etc. were missing in the GStreamer codec package.  After installing VLC, I can still view Indeo 5 etc. in Xine, Totem, and MPlayer.  So you're correct that VLC does it's own thing.  And I think I can conclude that Xine, Totem, and MPlayer  share a codec library.

As I move forward with Ubuntu, the next challenge is getting my multimedia keyboard to work I've had success with Keytouch, but the next/previous, stop, pause/play only work in Rhythm Box.  I wasn't sure if they should work in the various video players.  This is probably a topic for a new thread.

Anyway, I've made progress and I'm understanding some of the concepts.  Thanks for all the suggestions.

---

### Post by dancingmonkey on 2008-03-27
I have also been reading through a lot of the forums for answers and find most of them going on about code.  I am a simple user, and this is the first post I have found with simple  answers.  Thanks all for this usefull thread.

---

### Post by timsinger on 2008-03-27
Thanks! I now have full DVD support in Totem again...weird.

---

