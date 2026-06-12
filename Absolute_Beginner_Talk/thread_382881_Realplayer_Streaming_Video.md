---
title: "Realplayer Streaming Video"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Fidelio on 2007-03-12
Hi, 
Does anyone know how I can watch bbc video streams?
I installed Realplay which lets me use the 'listen again' facility on the beeb for radio, but when I try to watch a video clip it won't start.
I tried installing Realplayer 10, but couldn't. I got an error telling me that it depended on xlib which is uninstallable.

---

### Post by bwallum on 2007-03-12
This worked for me. Follow it carefully.
[https://help.ubuntu.com/community/Re...2d5a51b3fb69e9](https://help.ubuntu.com/community/Re...2d5a51b3fb69e9)

I'm watching BBC News now (Ubuntu 6.10)

---

### Post by bwallum on 2007-03-12
Belay that last transmission, I screwed up...

---

### Post by bwallum on 2007-03-12
You need to follow this page carefully. Run the code in your terminal (Applications>Accesories>Terminal). Look further down the page and view 'streaming video'  Make sure you follow the link and install 'w32codecs' as well. 

[https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9](https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9)

Come back if you get stuck, i went through this loop a week ago, no expert but happy to help as best I can.

Rgds
Bob

---

### Post by bwallum on 2007-03-12
&*%"£$..... the link gets automatically shortened so will not make any sense.

I'll walk you through it if you're there.

Rgds
Bob

---

### Post by bwallum on 2007-03-12
First install w32dodecs 

run this code in your terminal Applications>Accessories>Terminal

```
wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

Then install Xine
System>Admin>Synaptic Package Manager.
search for xine then click on the check box in the right hand window when you find totem-xine. It will offer 'mark for installation' Click on it and then Click on Apply. A number of files will be loaded.

That should be you. Go and test with BBC News. get back to me if stuck.

Note that there are more than one route to get you there. You could use gsteamer instead of xine. you could also go for the Real Player plugin. I went for Xine and totem because they were recommended to me.

Kind Regards
Bob

---

### Post by Fidelio on 2007-03-12
Hey, thanks. I haven't time to try this now, but I'll let you know how it goes.

---

### Post by bwallum on 2007-03-12
It will take about 10-20minutes...depending on your connection speed.

---

### Post by Fidelio on 2007-03-13
Thanks for the help. I've done all that, and I'm nearly there.
If I click on the video link in Firefox, it still doesn't play, but if I click 'open in standalone player' it downloads a link to my desktop. If i open this with realplayer I get the stream.
If I change the default program for .ram files to realplayer, it won't open. I have to right click and choose open with. This is sort of annoying.
How can I get it to open directly from the firefox link? Is it something like a setting in Firefox?
cheers.

---

### Post by bwallum on 2007-03-13
right...
Please bear with me I'm a newbie too.
What may have happened is that Firefox sees Totem as the media player and although you may have installed Real Player Firefox only looks at the first player it comes to.

To test this type 'about:plugins' into Firefox and check the list. Does RealPlayer appear as the first in the list to handle ram files?

I went down the Xine route so have no experience using Real Player (I use Firefox 2.0.0.2, Totem, gXine and then choose Windows Media Player setting to watch BBC News). I can point you to:-
 [https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods)

If you can't get anywhere having viewed the Firefox list and the docs then try starting a new post specifically targeted at Real Player advice. I'm sorry I'm not experienced enough to take you through Real Player set up but this Community will sort you out, they are very good.

If all else fails I will muddle through the docs with you.

Kind Regards
Bob

---

### Post by bwallum on 2007-03-13
plugins...I think the smiley popped in with a colon, letter P...command line for a smiley...ee, this Linux stuff.

key in 'Firefox' then a colon then 'plugins'

---

### Post by bwallum on 2007-03-13
hows it going?

---

### Post by panch0 on 2007-03-14
For Firefox the best video plugin is called mplayerplug-in. It uses MPlayer engine, so try it and let me know how it works for you.

---

### Post by atlien on 2007-03-18
I can't get streaming in Real Player either.  I tried the mplayer plugin before moving on to real player.  Had no luck with it either. 

This is puzzling.  How could Realplayer not be able to handle a Realplayer stream????
I am using Realplayer version 10.0.0.805 (Gold) with Ubuntu Edgy.

Any advice anyone?

---

### Post by geezerone on 2007-03-27
I am having problems with firefox 2 playing bbc streams via realplayer or mplayer plugin. With realplayer a white screen is all that shows and with mplayer a line of text connecting to website is all that happens.

---

### Post by notoriousdbp on 2007-04-18
I'm having the same problem.  When I open a video link on the BBC website it looks as though it's going to open normally, but when it's just about to start buffering, the real player section of the window just turns into a grey box.  Really frustrating.

---

### Post by geezerone on 2007-04-25
Anyone help?

---

### Post by Son of Silas on 2007-11-06
I had this on my 'real' Gutsy laptop. Unfortunately I am a complete and utter linux/ubuntu noob, so I don't know exactly how I fixed it. I installed Helix, that didn't work, installed Real Player, that didn't work. tried uninstalling both, that didn't work. I gave up completely.

A couple of days later, it worked. I've no idea how or why, although in the days in between i did get prompted to install some updates. I don't know what they were for (i wasn't paying attention) but now it works.

I'm currently typing this from my 'just built' VMWare Gutsy client running on Windows XP using the free VMWare Player. I have exactly the same problem. No streaming video with exactly the symptoms you describe. If anyone has any ideas I would be really really grateful...

---

