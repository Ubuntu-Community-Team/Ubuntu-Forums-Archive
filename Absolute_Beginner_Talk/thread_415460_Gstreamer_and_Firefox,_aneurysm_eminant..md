---
title: "Gstreamer and Firefox, aneurysm eminant."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Comzee on 2007-04-20
Ok, I really want to stream media that would usually be played with WMP on XP.

I think these are the instructions to do it, but they don't give enough detail.

>  Ubuntu

There are a variety of plugins that allow you to play streaming video in your browser. The recommended plugin is totem-xine-firefox-plugin. First, install the Windows Codecs, then install the totem-plugin.

On Ubuntu, Totem can use either the gstreamer (default) or xine multimedia frameworks. The plugin installation process depends on the framework you use. If you use totem-gstreamer (the version of Totem that uses the gstreamer back-end), install the totem-gstreamer-firefox-plugin package. If you use totem-xine, install the totem-xine-firefox-plugin package. 

I checked and I have the gstreamer Windows codecs. But I have no idea how to make gstreamer play media in Firefox. They say>  install the totem-gstreamer-firefox-plugin package but I have no idea how to install it?????? If anybody could give me some advice or some codes to install the player for Firefox that would be great.

Oh, and I installed every Gstreamer package from synaptic so I'm not missing anything.

---

### Post by Comzee on 2007-04-20
Come on, I've seen alot of people talk about how they have totem play streaming media in Firefox.
Any help here?

---

### Post by ghandi69_ on 2007-04-20
Sorry man, I have been able to stream most everything I need(... ok.. just porn) through VLC media player.  Thats all the farther I have gone.

---

### Post by Comzee on 2007-04-20
Great, I don't care what player i use. How do I get VLC to stream media in Firefox.

---

### Post by ammark on 2007-04-20
I have a similar issue, although its not GStreamer specific.

I installed Feisty yesterday, and previously I was using Dapper.... Right now I want to set up mplayer as my default player/plugin in Firefox... it seems that its set to totem.

I did a mozilla-mplayer plugin install and this is what it says now when I repeat it 

```
:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mozilla-mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 
``` 

But it is still playing totem. I went to Firefox's Edit>Preferences>Content>File Types, and except for "SPL" (shockwave flash) there's no other format listed.

How do I now getting about to configure MPlayer to play embedded media in Firefox?

---

### Post by Comzee on 2007-04-20
I really don't care what I use. I just want to be able to play WMP media on Ubuntu through Firefox.

---

### Post by JT673 on 2007-04-20
Try EasyUbuntu...It's a small GUI that downloads the codecs for you...

---

### Post by Comzee on 2007-04-20
I tried that easyUbuntu. It didn't seem to do anything. Then I installed VLC plugin for Firefox. All it says when I try to play embedded video is "no video". :mad: :mad: :mad: :mad: :mad:

---

### Post by dafoo21 on 2007-04-20
> **Comzee said:**
> I tried that easyUbuntu. It didn't seem to do anything. Then I installed VLC plugin for Firefox. All it says when I try to play embedded video is "no video". :mad: :mad: :mad: :mad: :mad:

Just wait for the "no video" to go away, itll eventually go away. That is sorta like a buffering screen.  It sounds like you might be trying to use mlb.tv. If you are not trying to use mlb.tv, then what youre trying to do is the same process I go throught trying to watch it.  Itll say No video then i just wait it out because the video is actually buffering and then itll eventually play. It also helps to get rid of any other plugin files in the /usr/mozilla-firefox/plugins directory that have totem in them.  Also, uf you have mplayer plugins in the folder, u would want to get rid of those if you are gonna use the VLC player.  You would want to get rid of the VLC plugin files if you are gonna use Mplayer as your player.

---

### Post by ghandi69_ on 2007-04-23
> **dafoo21 said:**
> Just wait for the "no video" to go away, itll eventually go away. That is sorta like a buffering screen.  It sounds like you might be trying to use mlb.tv. If you are not trying to use mlb.tv, then what youre trying to do is the same process I go throught trying to watch it.  Itll say No video then i just wait it out because the video is actually buffering and then itll eventually play. It also helps to get rid of any other plugin files in the /usr/mozilla-firefox/plugins directory that have totem in them.  Also, uf you have mplayer plugins in the folder, u would want to get rid of those if you are gonna use the VLC player.  You would want to get rid of the VLC plugin files if you are gonna use Mplayer as your player.

Have you gotten MLB.TV to work in Ubuntu???

---

### Post by trippinnik on 2007-05-13
try 
gksudo nautilus /usr/lib/firefox/plugins

then clear out the plugins you don't want to use.  you probably have mplayer ones, and i haven't had any luck using them with the mlb site.  leave libtotem plugins.  you can repeat the process to try different plugins, install the plugin you want to try and delete the others.

---

