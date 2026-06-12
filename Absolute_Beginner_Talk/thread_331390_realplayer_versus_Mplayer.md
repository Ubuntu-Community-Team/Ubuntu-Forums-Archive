---
title: "realplayer versus Mplayer"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by senorian on 2007-01-04
I listen to the BBC radio  plays; using Opera, which uses real player. The real player window is small and has a button that slides along a bar. If I only want to hear the last part of a play I just mouse over the button and hold a  left click and slide the button towards the end of the bar.Also the original BBC window stays open and I can scroll down it while still listening to the play.

However when I use either FF or Konqueror it is Mplayer that comes up. It occupies the whole screen (or at least half) and eliminates the BBC screen. Neither of these browsers  have a sliding button on a  bar, so they do not allow me to select the last part of a play .
This, for me, is a "killer".
Can I change which audio system is used with FF and Konq?
(Is edgy the same?)
Thanks
(using Kubuntu 6.06.1)

---

### Post by kd7swh on 2007-01-04
I know there is a way to get firefox to use realplayer rather than Mplayer by default. (can't remember) but there are several sites on "Setting up Media Plugins for Firefox on Linux"

Start here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Multimedia_Players_.26_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Multimedia_Players_.26_Browser_Plug-ins)

than checkout

[http://www.yolinux.com/TUTORIALS/LinuxTutorialMozillaConfiguration.html#APPLICATIONS](http://www.yolinux.com/TUTORIALS/LinuxTutorialMozillaConfiguration.html#APPLICATIONS)

the key will be making strings in about:config to make real player a helper application.

---

### Post by 900i on 2007-01-04
You need the mozilla-mplayer plugin, through Synaptic.

---

### Post by GMachine_24 on 2007-03-21
Well, first of all, he obviously HAS the Mplayer plug-in installed otherwise it wouldn't open when he clicks on a music link... right?

Besides, I have the same problem. Mplayer sucks. It just sits there saying it is 'buffering' and then 'buffers' for like 1 gb before I take a hammer and bash the crap out of my computer. This is RIDICULOUS.

Conversely, using RealPlayer is a breeze - just insert the url of the station you want to listen to - or rather the url of it's streaming site/connection - and you're off. Easy. Simple. AND IT WORKS.

However, I want to change the default Web music player to be RealPlayer as, I mentioned, MPLAYER SUCKS.

Thank you.

---

### Post by fakie_flip on 2007-03-21
Do you like totem? If you want to use totem, you should replace totem-gstreamer with totem-xine to have support for many more video and audio formats.

---

