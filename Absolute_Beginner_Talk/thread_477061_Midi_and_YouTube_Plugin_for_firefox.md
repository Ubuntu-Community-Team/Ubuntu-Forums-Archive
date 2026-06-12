---
title: "Midi and YouTube Plugin for firefox?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by bme on 2007-06-17
firefox cannot play midi files and cannot display youtube of websites that have those embedded...
Tried to install plugins but cannot find plugins...
How do I enable midi and youtube in ubuntu?

---

### Post by lamalex on 2007-06-17
well a) youtube isn't a format, youtube is a website that has user submitted content in the form of flash videos, so what you're looking for is flash player. look in add/remove programs

---

### Post by steveneddy on 2007-06-17
Read[ this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox").

---

### Post by bme on 2007-06-18
what about audio/midi files? in windows firefox uses quicktime. what is the quicktime plugin equivalent in ubuntu?

---

### Post by steveneddy on 2007-06-18
[Here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") is the top of the page I just sent you.

Read.....it will answer all of your questions.

---

### Post by bme on 2007-06-18
Youtube is ok now installed adobe flash...background music of sites stillnot working...installed totem gstreamer and mplayer,restarted firefox not effect...restarted pc no effect...how to configure firefox to play midi embedded? that is not explained on that link...

---

### Post by onero on 2007-06-18
> **bme said:**
> Youtube is ok now installed adobe flash...background music of sites stillnot working...installed totem gstreamer and mplayer,restarted firefox not effect...restarted pc no effect...how to configure firefox to play midi embedded? that is not explained on that link...

I have the mozilla-mplayer plugin installed, it's the firefox plugin for mplayer. You can also install it via Synaptic.

---

### Post by FuturePilot on 2007-06-18
Is there any way to play back embedded MIDIs? I've been trying to figure that out for quite some time now.

---

### Post by bme on 2007-06-18
> **onero said:**
> I have the mozilla-mplayer plugin installed, it's the firefox plugin for mplayer. You can also install it via Synaptic.
I have uninstalled and reinstalled mozilla-mplayer via apt-get but this has no effect on firefox NOT playing embedded background music in websites....

---

### Post by onero on 2007-06-18
> **bme said:**
> I have uninstalled and reinstalled mozilla-mplayer via apt-get but this has no effect on firefox NOT playing embedded background music in websites....

Do you have any other plugins installed? I used to have a problem wherein I had both totem-mozilla and mozilla-mplayer installed, and the two conflicted with each other. I removed totem-mozilla and just left the mplayer plugin.

---

### Post by swoll1980 on 2007-06-18
easy thing to do is get automatix 2 [www.getautomatix.com/](www.getautomatix.com/) once it installs just go to popular codecs click it and every thing will be cool. Ok?

---

### Post by bme on 2007-06-18
what difference will this automatix have on playing midi on firefox? sorry for this questionbut Ithink apt-get and synaptics are sufficient for installing purposes

---

### Post by gn2 on 2007-06-18
> **bme said:**
> what difference will this automatix have on playing midi on firefox? sorry for this questionbut Ithink apt-get and synaptics are sufficient for installing purposes

No difference to playing them, but installation process is made significantly simpler for codecs and suchlike by using Automatix.

---

### Post by loell on 2007-06-18
maybe you'd want to download the midi first and play it with ```
timidity
```

to install timidity in the command line

```
sudo apt-get install timidity
```

---

### Post by bme on 2007-06-18
> **loell said:**
> maybe you'd want to download the midi first and play it with ```
timidity
```

to install timidity in the command line

```
sudo apt-get install timidity
```

Kabayan,
I don't want to download midi-just want to listen to background music of the site...
try this site on firefox  [http://tagapikit.blogspot.com](http://tagapikit.blogspot.com) maybe you know some people there....

---

### Post by loell on 2007-06-18
> **bme said:**
> Kabayan,
I don't want to download midi-just want to listen to background music of the site...
try this site on firefox  [http://tagapikit.blogspot.com](http://tagapikit.blogspot.com) maybe you know some people there....

nice one :) 

truly > tagapikit gyud! :D




i'm not sure about this, but i think you're at a dead end, with playing embeded midi

with ubuntu +  firefox , and well, fewer sites this days have midi embeded on a page.

music sites these days would rather go for the fancy flash embeded music.

for further read on similar topic [http://forums.gentoo.org/viewtopic-p-4096298.html?sid=e2b7462dc89442e36ae8fafe70135669]("http://forums.gentoo.org/viewtopic-p-4096298.html?sid=e2b7462dc89442e36ae8fafe70135669")

---

