---
title: "listening to radio"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-09-18
I don't know how to articulate my question. i wanto to listen to radio online. I went to [http://www.sunriseradio.com/](http://www.sunriseradio.com/) but when i click on the listen live link Totem comes up. 

How can i switch Totem off? It doesn' t work on my system

How can i determine what plays what? For instance i believe Realplayer would work for me in this case but i don't know how to link the radio stn and realplayer together and stop Totem from kicking in.

many thanks in advance,


--
sophtpaw

---

### Post by XDevHald on 2005-09-18
[QUOTE=sophtpaw]I don't know how to articulate my question. i wanto to listen to radio online. I went to [http://www.sunriseradio.com/]("http://www.sunriseradio.com/") but when i click on the listen live link Totem comes up. 

How can i switch Totem off? It doesn' t work on my system

How can i determine what plays what? For instance i believe Realplayer would work for me in this case but i don't know how to link the radio stn and realplayer together and stop Totem from kicking in.

many thanks in advance,


--
sophtpaw[/QUOTE]
 Hmm, interesting, I am listening to Raj Kings radio right now from that link you gave me and using Totem. Do you have the gstreamer0.8 installed? There is a new version that released but is probably not compatible for hoary yet unless you have Breezy.

Check your gstreamer version and make sure it's up to date.

---

### Post by aysiu on 2005-09-18
I'm not in Gnome right now, but I think if you go to System > Preferences > Sound and Video, there should be something you can change.

---

### Post by sophtpaw on 2005-09-18
[QUOTE=Steve Myers]Hmm, interesting, I am listening to Raj Kings radio right now from that link you gave me and using Totem. Do you have the gstreamer0.8 installed? There is a new version that released but is probably not compatible for hoary yet unless you have Breezy.

Check your gstreamer version and make sure it's up to date.[/QUOTE]

Yes, i had gstreamer 0.8 installed. I am using Hoary i should specify. I went to Synaptics to confirm. I saw Totem Xine and installed that (i don't know what the difference is between that just Totem) and now at least Totem plays my CD's where it didn't before. So, that is an improvement, but it still doesn't play radio.

Any idea on the second part of my question how to delegate and specify what player one wants to do what. 

can i select realplayer for the radio instead of Totem automatically kicking in?
I think realplayer would do it.

thx

--
sophtpaw

---

### Post by XDevHald on 2005-09-18
To be honest with you, I have been trying to figure that out since I have been running Ubuntu, which is about 7 months now and still never got it :(

If anyone has figured this out, please post a reply, It could be something right under my nose and never found it.

---

### Post by sophtpaw on 2005-09-18
[QUOTE=aysiu]I'm not in Gnome right now, but I think if you go to System > Preferences > Sound and Video, there should be something you can change.[/QUOTE]


Thx Aysiu,

System/Preference/Removable Drives and Media

--
sophtpaw

---

### Post by XDevHald on 2005-09-18
[QUOTE=sophtpaw]Thx Aysiu,

System/Preference/Removable Drives and Media

--
sophtpaw[/QUOTE]
 The funny part to this is that I have been using this app for quite some time now and didn't ever take time to find it in there it until now :p

Thanks guys!

---

### Post by sophtpaw on 2005-09-18
[QUOTE=sophtpaw]Thx Aysiu,

System/Preference/Removable Drives and Media

--
sophtpaw[/QUOTE]


Still getting:

The address type is unknown or unsupported

mms://193.218.160.20/sunrise

??
Please help

--
sophtpaw

---

### Post by racecat on 2005-09-18
Don't know if this applies, but I had some luck with the "MediaPlayerConnectivity" extension for Firefox. It lets you select which players to use for what.

[https://addons.mozilla.org/extensions/moreinfo.php?id=446](https://addons.mozilla.org/extensions/moreinfo.php?id=446) 

Sorry if I'm talking out of turn. Hope this helps. This extension wasn't apparent until someone on a forum recommended it to me.

Bill

---

### Post by sophtpaw on 2005-09-18
[QUOTE=racecat]Don't know if this applies, but I had some luck with the "MediaPlayerConnectivity" extension for Firefox. It lets you select which players to use for what.

[https://addons.mozilla.org/extensions/moreinfo.php?id=446](https://addons.mozilla.org/extensions/moreinfo.php?id=446) 

Sorry if I'm talking out of turn. Hope this helps. This extension wasn't apparent until someone on a forum recommended it to me.

Bill[/QUOTE]

Thx Bill,

Please never feel like you are talking out of turn on my threads. Any help or possibility of help is welcome.

The link was interesting and through it i stumbled onto other extensions that are useful - so thx.

But it hasn't sorted out the radio reception. Totem still pops up automatically, it buffers but no sound except intermittently, for about 1/2 a sec every 10 -20 seconds. 

Any other recommendations out there, other than get another operating system, one that works?

Many thx in advance as usual,


--
sophtpaw

---

### Post by occy8 on 2005-09-18
first try
in the ubuntu guide
How to configure sound to work properly in GNOME 

then you could run the easyubuntu script from here
[http://www.ubuntuforums.org/showthread.php?p=358089](http://www.ubuntuforums.org/showthread.php?p=358089)

I used version 2.1 and it worked great 
I also use the "MediaPlayerConnectivity" extension for Firefox which lets you easiely change players and try which one works best. I'm using VLC.

on the downside I have also a station which doesn't work for me

[http://brafm.globalradios.com/low.asx](http://brafm.globalradios.com/low.asx)

its loading data but there is no sound just burp every now and then similar to what
sophtpaw reported.

---

### Post by Lambert on 2005-09-18
You may want to look into streamtuner for finding and listening to a radio stream.

If you do try it; the default player is xmms. You can click on edit>preferences and under the applications secition you'll see 'listen to a stream' You can change that to any program you like such as real player. 

I personally use rhythmbox to play radio streams. You can save the stream addresses there and just pull up rhythmbox to connect later.

---

