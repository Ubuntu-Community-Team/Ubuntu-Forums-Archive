---
title: "One player to rule them all, and then bind them!"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-12-01
**{One player to rule them all, and then bind them!}**
[COLOR="DarkGreen"]Lord of the ring [/COLOR]- That's how I want to feel right now after having had to troubleshoot for 3 days straight without immediate easy results.  Trying to just hear some sound from the different formats mp3, midi, quicktime, realplayer, etc. etc. without hassle.

As of now I basically have had to install a new program for each and every format.
1. mp3 = [ Totem Movie Player, Rythm Box (both preinstalled) ], xmms
2. midi = timidity
3. realplayer = Real Player 10
4. quicktime = mplayer
5. shoutcast+abacast = streamtuner ([COLOR="DarkGreen"]don't understand how to operate it?[/COLOR])

Thats like 7 different programs for 5 different formats and streams.  In Windows you had "Media Player Classic" along with the "K-lite Codec pack" that extracted all possible kinds of codecs into MPC.  Now isn't their something similar where you could just download a COMPLETE Codec pack for ONE media player in Linux?

---

### Post by jordanmthomas on 2006-12-01
I'm pretty sure that, after installing the appropriate codecs, mplayer will play pretty much **anything** you can throw at it.  VLC is known for its versatility as well.

---

### Post by mushroom on 2006-12-01
```
sudo apt-get install xmms-midi
```

Use that for midi support in XMMS.

All you need is XMMS and MPlayer; XMMS will play most (if not all) audio formats. MPlayer plays pretty much everything, and it includes a GUI (whose command, if it isn't in your menu, is "gmplayer"). As for shoutcast, I'm not entirely sure how that works, but there appears to be an XMMS plugin for that, too (xmms-liveice). Also, if you really want to consolidate all of those functions, you can grab "xmms-xmmplayer", which uses XMMS as a frontend for MPlayer. Hope that helps.

---

### Post by Brownedwg89 on 2006-12-01
vlc plays basically anything(video or audio)
but i would suggest using vlc for videos and amarok for audio, since amarok is so amazing

---

### Post by mushroom on 2006-12-01
I've found that MPlayer handles h.264 better, and it integrates with other apps. Also, it doesn't use really ugly widgets. Amarok is pretty great, but it's not a GNOME app, so you lose the benefits of integration, and Rhythmbox (which is a GNOME app) does much of what Amarok does.

---

### Post by jingo811 on 2006-12-02
> mike@sanka:~$ sudo apt-get install xmms-midi
Reading package lists... Done
Building dependency tree... Done
[COLOR="Red"]E: Couldn't find package xmms-midi[/COLOR]
mike@sanka:~$

Now what am I doing wrong?

and.....

> **jordanmthomas said:**
> I'm pretty sure that, after installing the appropriate codecs, mplayer will play pretty much **anything** you can throw at it.  VLC is known for its versatility as well.
I did this [http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Dapper#How_to_install_Multimedia_Codecs)
> sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base \
gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse \
gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse w32codecs

Still my mplayer can't play midi files.  What am I doing wrong?

---

### Post by Lord Illidan on 2006-12-02
> **jingo811 said:**
> Now what am I doing wrong?


Let me ask you one thing Sauron the Great...Can you send us a copy of your /etc/apt/sources.list file via Nazgul Airlines please?

---

### Post by jingo811 on 2006-12-02
1 character.
> [B]## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
[/B]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

**## MAJOR BUG FIX UPDATES produced after the final release**
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

**## UBUNTU SECURITY UPDATES**
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

**## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)**
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

**## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)**
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
                                                                                                                                          
[B]## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) [/B]
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

**#AUTOMATIX REPOS START**

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
#AUTOMATIX REPOS END

bump.

---

### Post by jingo811 on 2006-12-02
bump.

---

### Post by desimo on 2006-12-02
It should be available in the universe.

[http://archive.ubuntu.com/ubuntu/pool/universe/x/xmms-midi/](http://archive.ubuntu.com/ubuntu/pool/universe/x/xmms-midi/)

---

### Post by jingo811 on 2006-12-03
Do you mean that I should paste this into my sources.list?
> deb [http://archive.ubuntu.com/ubuntu/pool/universe/x/xmms-midi/](http://archive.ubuntu.com/ubuntu/pool/universe/x/xmms-midi/) dapper universe
I don't really know what to do with the link you gave me, my eyes are just 2 big (?_?) right now.

---

### Post by podunk on 2006-12-03
There may very well be something simple wrong here?

xmms is in synaptic on both my K/Ubuntu machines and plays damn near everything I use:
System
Administration
Synaptic Package Manager

Click the search button and type in xmms. There will be several plugins there also, I installed xmms-common and xmms-dev also.

If it's not in Synaptic then there is either something wrong with your sources.list file or maybe something screwy with your connection?

The only thing I see that differs from mine in your sources.list is that you removed the front end of the Automatix repo but left the back end in.

---

### Post by jingo811 on 2006-12-03
I couldn't find any xmms-common, only gxmms-common in synaptic:
> Common files for the gxmms (both XMMS and BMP) GNOME applet
This package includes files that are common between gxmms-xmms and
gxmms-bmp, like i18n mo files.

I installed xmms-dev and gxmms-common but I still can't open up a midi file in Xmms player.  Isn't there a comprehensive Tutorial out there that deals with making Xmms player able to play as many file types as Windows Winamp?
I've been beating around the bush with this annoying little codec problem for a while now.

---

### Post by jingo811 on 2006-12-05
bump number 2.

---

### Post by hotbrainz on 2006-12-05
hello jingo811,

I understand that u have tried a lot of things with xmms and i am not that wise to guide you around. I can suggest just one thing ...install "Amarok"..end of worries. I presume you have used automatix already. The two of those and "VLC media player".

You are sorted for both audio and video. I did that. Took me 15  min in all and i am able to able all file formats i have come across.

So maybe you can give it a shot.

Hope this helps.
Cheers

---

### Post by jingo811 on 2006-12-05
tnx for the tip.  But I'm having trouble finding Amarok in Automatix I guess it's because its an KDE something only.
I don't yet dare to mess with KDE for fear of loosing everything I've done in Gnome Desktop :-k Besides doesn't the implementations of KDE something add some more 200 Megs to your harddrive?

---

### Post by hotbrainz on 2006-12-05
I agree "amarok" is a KDE app. It does not mess anything in Gnome trust me on this. it is not in Automatix. You will find it in Synaptic package manager. Do you know how to use this. I can elaborate if you want

---

### Post by jingo811 on 2006-12-05
I know how to use Synaptic but I don't know which bits and pieces from KDE I should pick as a minimum to make things problem free.
And how to setup and install KDE without interfering or deleting all Gnome stuff by mistake, that you could elaborate more.

---

### Post by hotbrainz on 2006-12-05
> **jingo811 said:**
> I know how to use Synaptic but I don't know which bits and pieces from KDE I should pick as a minimum to make things problem free.
And how to setup and install KDE without interfering or deleting all Gnome stuff by mistake, that you could elaborate more.
Amarok works fine in Gnome. Just choose amarok and it will pick up the dependencies automatically. You need no KDE bits in Amarok. I am using it with gnome.

---

### Post by Sef on 2006-12-05
> know how to use Synaptic but I don't know which bits and pieces from KDE I should pick as a minimum to make things problem free.
And how to setup and install KDE without interfering or deleting all Gnome stuff by mistake, that you could elaborate more.

The other option is to install it via the Terminal. (Applications > Accessories > Terminal)

Just use aptitude when installing and if you choose to uninstall it, aptitude will remove all the dependcies.

```
sudo aptitude install amarok
```

---

### Post by jingo811 on 2006-12-05
Well Amarok is installed now.  But I still can't play midi files on this sort of intuitive GUI players.  I'm still missing the neccessary midi codecs for all my 8 different media players.

What should I do now?

---

### Post by jingo811 on 2006-12-07
bump 3.
I'm gonna rephrase my questions since things got off-tracked when ppl keep suggesting new programs to solve my problems.  Instead of giving me codec install Tutorial on my now 8 existing media players.

**This is regarding XMMS>>>**
> Do you mean that I should paste this into my sources.list?
Quote:
deb [http://archive.ubuntu.com/ubuntu/poo...e/x/xmms-midi/](http://archive.ubuntu.com/ubuntu/poo...e/x/xmms-midi/) dapper universe
I don't really know what to do with the link you gave me :confused: 
> 
I couldn't find any xmms-common, only gxmms-common in synaptic:
[QUOTE]Quote:
Common files for the gxmms (both XMMS and BMP) GNOME applet
This package includes files that are common between gxmms-xmms and
gxmms-bmp, like i18n mo files.
I installed xmms-dev and gxmms-common but I still can't open up a midi file in Xmms player. Isn't there a comprehensive Tutorial out there that deals with making Xmms player able to play as many file types as Windows Winamp?
I've been beating around the bush with this annoying little codec problem for a while now.[/QUOTE]

---

### Post by jingo811 on 2006-12-13
no stable solution yet from the Xmms group ey? :-k

---

### Post by Perfect Storm on 2006-12-13
Well, you could compile audacious with midi support, though it's a big step if you are new.

[http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)

---

### Post by ekricyote on 2007-08-31
The extra plugins package for Audacious seems to have Timidity support already. Although I'm having trouble wiring it to play my own personal soundfonts, the default seems to play just fine.

The kewl thing about Audacious is it plays SPCs; if you like the 16-bit video game console era, you'll love the support for that file format.

If anyone has made Timidity play with a soundfont (I'm using Reality 32MB GM/GS on an Audigy) to play MIDI files, I'm all ears. I got Kmid to work with it (as well as aplaymidi), but no juice on Audacious.

As a side note for video files, since I use VLC and Totem to play video (although Totem is not as smooth when playing MKVs), Audacious fills my niche for audio files quite nicely. Still, it would be great to have Totem play a smooth MKV; the GUI does it perfectly for me. I prefer having two different players, one for sound (compact), and the other for video.

---

