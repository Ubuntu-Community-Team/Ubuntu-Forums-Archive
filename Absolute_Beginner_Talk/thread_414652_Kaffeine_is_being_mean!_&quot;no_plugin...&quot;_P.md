---
title: "Kaffeine is being mean! &quot;no plugin...&quot; Please help!"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Yes_It's_Me on 2007-04-20
Well, i got my tv tuner working on feisty by typing sudo modprobe cx88-dvb in the terminal to enable the kernel modules. But in the final release when i do the same thing it allows kaffeine to recognize it and search for channels etc but when playing a channel all i get is a black screen with the message:

No plugin found to handle this resource (/home/ubuntu/.kaxtv.ts)

then under "details" it says:

05:52:30 AM: xine: couldn't find demux for >/home/ubuntu/.kaxtv.ts<
05:52:30 AM: xine: found input plugin : file input plugin
05:52:30 AM: video_decoder: no plugin available to handle 'XviD'
05:52:30 AM: xine: found demuxer plugin: AVI/RIFF demux plugin
05:52:30 AM: xine: found input plugin : file input plugin

Please help, this is being a pain in the ***! dapper and edgy would play it out of the box but in feisty all i've had is problems with it!

---

### Post by JT673 on 2007-04-20
You don't have the DivX/XviD codecs installed.  Go to System -> Admin -> Synaptic, and search for any Xvid codecs you might have not installed.

If you're using KDE, there's the kdetv program...I'm not sure about TV tuning...

---

### Post by Yes_It's_Me on 2007-04-20
when i do that, most things are already installed, the only ones that are not are .dev or .src files etc.

---

### Post by Bachstelze on 2007-04-20
Perhaps Xine just can't handle this type of streams. Did you try another player ?

---

### Post by Yes_It's_Me on 2007-04-20
all other tv viewers i have found for linux either don't install/launch or don't scan for channels, and don't help out when trying to make a channels file.

kaffeine is the only one i have been able to get going that (used to) work fine.

---

### Post by Yes_It's_Me on 2007-04-20
please guys! i need to get this bloody thing going.

---

### Post by Yes_It's_Me on 2007-04-20
:(

---

### Post by ahabahab on 2007-04-23
I've got the same problem after updating to Ubuntu 7.04.  But I installed libxine1-plugins package and now Kaffeine works fine!  (Before I installed libxine1-kde but this was unnessessary, I think). Hope this helps you too.

---

### Post by TrompeLaMort on 2007-06-03
I had the same problem, went into the adept manager, did a search for libxine, and installed the plugins package and a couple of others I was missing, and now it works...

---

### Post by mr_boo1711 on 2007-06-04
I'm having the same issue!

Exactly the same error message coming up on my screen.  Haven't tried any of the above suggestions yet, but I will do when I get in from work and then post my results here...

For the record - I'm using a DVB Freecom USB tuner.  It scans fine, it just wont display any audio/video. :(

---

### Post by mr_boo1711 on 2007-06-04
Thanks to everyone above!  Worked a treat.  Used the Synaptics manager and installed the libxine plugins... job done.  Another hurdle overcame.

:D :D

---

### Post by neurobunnie on 2007-07-19
Hey.. 

This is the first time i've *ever* posted in a forum but..

i'm getting this same message too when running kaffeine --verbose.  my system has worked fine for months and then earlier today while surfing the web and watching some embedded videos, my computer crashed.  my whole xserver just went away and looks like it restarted, but now i get no video, but i do get sound in my videos..

not sure how to fix this.  tried reinstalling every libxine i could find except for debug ones.. i know i've installed the w32codecs, ubuntu restricted codecs, i have a /usr/lib/win32 and in my kaffeine - configure xine it's pointing to there and to /usr/lib/codecs..

i have no idea how to fix this..

Thanks for anyone's help

---

### Post by sailor2001 on 2007-07-19
if you are using firefox, you have to install greasemonkey as an addon....also search forum for grease monkey as there is a little script to put in there.

---

### Post by neurobunnie on 2007-07-19
i'm trying to watch videos using kaffeine though, not as a plugin to firefox or anything.  in vlc, the video still works but the audio is very scratchy..

---

