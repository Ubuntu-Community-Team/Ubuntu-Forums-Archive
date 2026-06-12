---
title: "can't watch some videos in firefox (got codecs/got mplayer/got flash/got plugin)"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by econmit on 2007-10-29
Hi,

I'm a recent convert to Ubuntu and I'm still loving it.

But I have some problems getting video to work on firefox from all web sources. I managed to get youtube and other video streams like nytimes work.

But, for example, I cannot watch:
[http://cosmos.bcst.yahoo.com/up/player/popup/?rn=1929371&ch=1929371&src=ukeurosport](http://cosmos.bcst.yahoo.com/up/player/popup/?rn=1929371&ch=1929371&src=ukeurosport)
Nor the video on the right here:
[http://uk.eurosport.yahoo.com/](http://uk.eurosport.yahoo.com/)
nor any provided here
[http://www.atpmastersseries.tv/page/Home/0,,11444,00.html](http://www.atpmastersseries.tv/page/Home/0,,11444,00.html)

So the pattern seems to be that I can see flash video but not windows media player video. [I know that my macromedia plugin seems to be fine.]

I have installed all the codec packages like the ubuntu dirty one and also (when things didnt work) individually installed some codecs and plugins following the instructions at:
[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html)
to install codecs and the firefox plugin.

Any ideas? Many thanks!

---

### Post by philinux on 2007-10-29
The first 2 sites you mention use the Flash plugin and work fine for me.

The third site is **premium tv** you need to set up an account see bottom of their page.

---

### Post by econmit on 2007-10-29
> **philinux said:**
> The first 2 sites you mention use the Flash plugin and work fine for me.

The third site is **premium tv** you need to set up an account see bottom of their page.

No, that's not it. The sites #3-#5 that I listed are all examples of video that does not work in Firefox using Ubuntu for me. But it is not due a missing account! Indeed, for sites 3-4, I have a Yahoo account and i am logged in. Moreover, these videos play in my Windows Firefox setup.  In fact, site #5 has no account required whatsoever and it does not work. 

So the pattern I see is that these are video that uses windows media player in windows/firefox. For these, I cannot watch it on my Ubuntu 7.10/ Firefox setup. Despite having install codecs, players and plugins....

Anyone have any suggestions?

---

### Post by carlosjuero on 2007-10-29
> **econmit said:**
> No, that's not it. The sites #3-#5 that I listed are all examples of video that does not work in Firefox using Ubuntu for me. But it is not due a missing account! Indeed, for sites 3-4, I have a Yahoo account and i am logged in. Moreover, these videos play in my Windows Firefox setup.  In fact, site #5 has no account required whatsoever and it does not work. 

So the pattern I see is that these are video that uses windows media player in windows/firefox. For these, I cannot watch it on my Ubuntu 7.10/ Firefox setup. Despite having install codecs, players and plugins....

Anyone have any suggestions?

The links (that didn't require an account) worked fine for me, I had an odd screen flicker when I clicked the first one (screen went black and returned) - but the video played. Have you installed the 'Restricted Codecs'?

---

### Post by econmit on 2007-10-29
> **carlosjuero said:**
> The links (that didn't require an account) worked fine for me, I had an odd screen flicker when I clicked the first one (screen went black and returned) - but the video played. Have you installed the 'Restricted Codecs'?

Good, so this proves the point that something is wrong on my end.

Yes, from what I know I have all the necessary codecs. If anyone knows exactly what I should check for (and maybe even explain how  exactly to do that---what to type into command line or what to search in synapticcs---since I am a newbie), I'd be happy to report back.

Thanks for any help in advance. I really appreciate this great community.

---

### Post by carlosjuero on 2007-10-29
> **econmit said:**
> Good, so this proves the point that something is wrong on my end.

Yes, from what I know I have all the necessary codecs. If anyone knows exactly what I should check for (and maybe even explain how  exactly to do that---what to type into command line or what to search in synapticcs---since I am a newbie), I'd be happy to report back.

Thanks for any help in advance. I really appreciate this great community.

Hrm - all I did for codecs is 1) Install VLC (that adds a bunch of codecs from what I understand), and 2) Open up the Add/Remove Programs and install the 'Restricted Codecs' by adding the 'Ubuntu restricted extras'

---

### Post by econmit on 2007-10-29
> **carlosjuero said:**
> Hrm - all I did for codecs is 1) Install VLC (that adds a bunch of codecs from what I understand), and 2) Open up the Add/Remove Programs and install the 'Restricted Codecs' by adding the 'Ubuntu restricted extras'

Thanks Carlos, but unfortunately that didn't work for me:

1. I checked synaptics and have "Ubuntu restricted Extras" already ( I'm pretty sure I can't see it from add/remove though)

2. I did 
sudo aptitude install vlc
and added vlc but that didn't fix anything.

Any other ideas anyone? Much appreciated

---

### Post by philinux on 2007-10-29
In your first post you only mention 3 sites. 

```
But, for example, I cannot watch:
http://cosmos.bcst.yahoo.com/up/play...rc=ukeurosport
Nor the video on the right here:
http://uk.eurosport.yahoo.com/
nor any provided here
http://www.atpmastersseries.tv/page/...,11444,00.html

```

Like I said before the first two are flash the third one requires an account.

you mention other sites but dont list them so we can check whats going on. :confused:

---

### Post by Maestro23 on 2007-10-29
Go over your Restricted Formats again. Migh be  somthing you missed.[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Restricted%29%7C%28Formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Restricted%29%7C%28Formats%29)

---

### Post by ecoxmit on 2007-10-29
philinux, 

the first site he links to
       [http://cosmos.bcst.yahoo.com/up/play...rc=ukeurosport](http://cosmos.bcst.yahoo.com/up/play...rc=ukeurosport)
uses mplayer (at least in my computer) to play the video (not flash).

econmit  (wow, similar name!),

The link seems to be playing fine in my computer using the mplayer firefox plugin. But i am not sure how you tell firefox to use the mplayer one instead of default.

---

### Post by econmit on 2007-10-29
> **philinux said:**
> In your first post you only mention 3 sites. 

```
But, for example, I cannot watch:
http://cosmos.bcst.yahoo.com/up/play...rc=ukeurosport
Nor the video on the right here:
http://uk.eurosport.yahoo.com/
nor any provided here
http://www.atpmastersseries.tv/page/...,11444,00.html

```

Like I said before the first two are flash the third one requires an account.

you mention other sites but dont list them so we can check whats going on. :confused:

Thanks for trying to help. These are the sites I have detected the problem at. So the first 2 on this list I cannot get to work! Despite having the flash plugin... The third site does not require a user to view the video that comes out on the right [a user is only required to get live full games]. But forget that site if you want. 

The first 2 don't work for me and they do (apparently) for you. I have a problem.

---

### Post by philinux on 2007-10-29
right ok I always have flash block enabled , never mind.

In the address bar of firefox type
```

about:plugins
```

Have a look whats installed  here's mine showing shockwave and mplayer.

---

### Post by econmit on 2007-10-29
I attach my about:plugin page from firefox (copied into OPenOffice and exported as PDF)

---

### Post by sailor2001 on 2007-10-29
if using firefox......add-on "media wrap" "mediaplayer connectivity" and "fast video download"

---

### Post by philinux on 2007-10-29
That explains it all you've got totem plugin installed as well which causes a conflict.
go to synaptic and uninstall totem-mozilla plugin.

---

### Post by econmit on 2007-10-29
Here is my about plugin pages as png screenshots (it took 5 to get the whole list).

As you can see I have a lot of plugins! Maybe that is the problem?

---

### Post by econmit on 2007-10-29
> **philinux said:**
> That explains it all you've got totem plugin installed as well which causes a conflict.
go to synaptic and uninstall totem-mozilla plugin.

Thanks a lot, that worked! 

So apparently the totem plugin does not work so well. it wouldn't play those videos before I installed mplayer; and then wouldn't let mplayer do its thing when I did install the latter. With just the mplayer plugin everything seems fine for now.

---

### Post by reza81 on 2007-10-29
You also can download a very handy extention for firefox & watch everything fullscreen outside of your browser. You also can download the files & or stream. Watch it in any player you want.

 Get "MediaPlayerConnectivity" !!!

Tools >> Add-ons >> get ubuntu add-ons 

search for MediaPlayer & install MediaPlayerConnectivity.

restart firefox & there you go.

---

