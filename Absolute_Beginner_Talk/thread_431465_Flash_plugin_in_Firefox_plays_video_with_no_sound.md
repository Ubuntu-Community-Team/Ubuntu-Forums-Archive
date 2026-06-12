---
title: "Flash plugin in Firefox plays video with no sound"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-05-03
If I go to, say, youtube, and click on a flash video, I see the video, but it is silent.  Are their any settings somewhere that need tweaking?

---

### Post by mikeyphi on 2007-05-03
Have a look under System - Preferences - Sound

Try a few different settings.  Good luck!

---

### Post by deadgobby on 2007-05-03
Do you have a sound card? If you have a sound card. You may need to go into your BIOS and disable the on board sound card. After the on board sound card is disabled. All sounds will go through the sound card.
Gobby

---

### Post by Compyx on 2007-05-03
I have noticed on a few systems (specifically laptops) that ESD doesn't work well with Flash Video, so you might try disabling ESD under System -> Preferences -> Sound -> "Sounds" tab.

---

### Post by Delkster on 2007-05-03
> **ubnewbie2 said:**
> If I go to, say, youtube, and click on a flash video, I see the video, but it is silent.  Are their any settings somewhere that need tweaking?

Which version of the flash player are you running? Ubuntu 6.06 LTS (a.k.a. Dapper) probably comes with Flash Player 7.x by default but the recent Ubuntu 7.04 (Feisty) release has Flash Player 9.x. The two use different sound output systems so it might be useful to know which one you're using.

You can find out the player version you're using by right-clicking on a flash animation to bring up a menu.

---

### Post by ubnewbie2 on 2007-05-03
> **deadgobby said:**
> Do you have a sound card? If you have a sound card. You may need to go into your BIOS and disable the on board sound card. After the on board sound card is disabled. All sounds will go through the sound card.
Gobby


Are you sure?  All other apps play sounds, mp3s movies etc, quite well.  The sound system is working fine, except for playing .swf files with the flash plugin in Firefox

---

### Post by ubnewbie2 on 2007-05-03
> **Delkster said:**
> Which version of the flash player are you running? Ubuntu 6.06 LTS (a.k.a. Dapper) probably comes with Flash Player 7.x by default but the recent Ubuntu 7.04 (Feisty) release has Flash Player 9.x. The two use different sound output systems so it might be useful to know which one you're using.

You can find out the player version you're using by right-clicking on a flash animation to bring up a menu.

I am running a fairly new feisty install and it is Flash 9

---

### Post by ubnewbie2 on 2007-05-03
> **Compyx said:**
> I have noticed on a few systems (specifically laptops) that ESD doesn't work well with Flash Video, so you might try disabling ESD under System -> Preferences -> Sound -> "Sounds" tab.

Just tried it, no luck.  I also tried setting all the sounds to use alsa, instead of auto, still no luck.

---

### Post by ubnewbie2 on 2007-05-03
I just installed opera, and, yes, same problem there.  So I guess it's Flash Player that is the problem for sure.

---

### Post by organic brian on 2007-05-11
I'm having the same issue, on each computer I've tried Ubuntu on.  Sound in general works, but not for Flash videos.

An example system (the oldest and most factory-stock):
- Dell Dimension XPS T450
- Ensoniq ES1370 PCI audio card
- Ubuntu 7.04, downloaded

I have tried all of the steps in this article for enabling multimedia:
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

I have tried re-detecting the sound card, and using various settings for Sound in the System > Preferences > Sound.

This is apparently caused by a bug, and having to do with the design of Flash and the way the audio codecs vie for the attention of the sound hardware:
[https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760)
I tried some of the suggestions on this thread, including the three-line solution by Daniel Carrera, but none of them worked for me.

Ideas?

  - Brian

---

### Post by ubnewbie2 on 2007-05-11
> **organic brian said:**
> I'm having the same issue, on each computer I've tried Ubuntu on.  Sound in general works, but not for Flash videos.

An example system (the oldest and most factory-stock):
- Dell Dimension XPS T450
- Ensoniq ES1370 PCI audio card
- Ubuntu 7.04, downloaded

I have tried all of the steps in this article for enabling multimedia:
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

I have tried re-detecting the sound card, and using various settings for Sound in the System > Preferences > Sound.

This is apparently caused by a bug, and having to do with the design of Flash and the way the audio codecs vie for the attention of the sound hardware:
[https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760)
I tried some of the suggestions on this thread, including the three-line solution by Daniel Carrera, but none of them worked for me.

Ideas?

  - Brian

My system is home built but uses a 1370 audio card too.

I see that the bug report says a fix has been released for the non-free flash plugin.  How do I get this fix and is it easy to apply?

---

### Post by jjbean on 2007-05-15
If you haven't got your problems fixed yet, this thread shows what I did ti fix it.

[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=443157]("http://ubuntuforums.org/showthread.php?t=443157")[/COLOR]

It worked for Opera as well, but like I said in the other thread sound lags at times.

Hope this helps.

---

### Post by ubnewbie2 on 2007-05-15
> **jjbean said:**
> If you haven't got your problems fixed yet, this thread shows what I did ti fix it.

[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=443157]("http://ubuntuforums.org/showthread.php?t=443157")[/COLOR]

It worked for Opera as well, but like I said in the other thread sound lags at times.

Hope this helps.


Thanks for the suggestion, unfortunately installing pulse, and in particular the esound-compat bit, necessitates removing esound (according to Synaptic).  This breaks lots of other things, such as sounds in gnome, xmms, rhythmbox etc

It does get flash making sound though :)   I'm just not ready to lose all the other sounds to get it :(

---

### Post by Delkster on 2007-05-15
> **ubnewbie2 said:**
> Thanks for the suggestion, unfortunately installing pulse, and in particular the esound-compat bit, necessitates removing esound (according to Synaptic).  This breaks lots of other things, such as sounds in gnome, xmms, rhythmbox etc

It does get flash making sound though :)   I'm just not ready to lose all the other sounds to get it :(

If Rhythmbox loses sound output when you uninstall esound, try changing the gstreamer audio sink to something else than ESD. You can find the settings with the command gstreamer-properties (it was removed from the menu at some point in the name of simplicity or something). Change the audio output sink from ESD to ALSA and see if it works.

XMMS has a similar setting for the sound output system in its preferences.

Or you could try installing the pulseaudio-esound-compat package which, according to the package description, should allow PulseAudio to be compatible with ESD. I haven't tried it, though, and don't know how it works.

Edit: sorry, looks like I was too careless reading your message. Anyway, the former advice still applies -- you could try outputting to something else than ESD from gstreamer and XMMS.

---

### Post by jjbean on 2007-05-15
Sorry for the late reply. I had to work a 12 today. Anyway my sound crapped out after a reboot. So I did more Google work. This has all my sounds working and syncing correctly. Including .mp3, .oog, etc in all my apps.
I have video with sound in Firefox, Opera, and IE6. My video and music players work fine. The only sounds I do not have is the login and logout music. The little drum roll on the login screen does work.

Install these packages: 
  pulseaudio
  pulseaudio-esound-compat
  libgstreamer-plugins-pulse0.1C
  libpulse-browse0
  libpulse-mainloop-glibo

I had to add myself to these groups:
  pulse
  pulse-rt
  pulse-access

Go to System > Preferences > Sound > Sound Tab. Make sure that Sound Events, Music and Movies, and Audio Conferencing are in **_Autodetect_**.

Make sure you leave ESD _**enabled**_ under System > Preferences > Sound  >Sound Tab.

Install the .deb file from this page. [COLOR="Red"][http://pulseaudio.revolutionlinux.com/PulseAudio]("http://pulseaudio.revolutionlinux.com/PulseAudio")[/COLOR]

Reboot.

I hope this helps some of you out. It worked well for me, but I cannot make any guarantees.

---

### Post by ubnewbie2 on 2007-05-16
> **jjbean said:**
> Sorry for the late reply. I had to work a 12 today. Anyway my sound crapped out after a reboot. So I did more Google work. This has all my sounds working and syncing correctly. Including .mp3, .oog, etc in all my apps.
I have video with sound in Firefox, Opera, and IE6. My video and music players work fine. The only sounds I do not have is the login and logout music. The little drum roll on the login screen does work.

Install these packages: 
  pulseaudio
  pulseaudio-esound-compat
  libgstreamer-plugins-pulse0.1C
  libpulse-browse0
  libpulse-mainloop-glibo

I had to add myself to these groups:
  pulse
  pulse-rt
  pulse-access

Go to System > Preferences > Sound > Sound Tab. Make sure that Sound Events, Music and Movies, and Audio Conferencing are in **_Autodetect_**.

Make sure you leave ESD _**enabled**_ under System > Preferences > Sound  >Sound Tab.

Install the .deb file from this page. [COLOR="Red"][http://pulseaudio.revolutionlinux.com/PulseAudio]("http://pulseaudio.revolutionlinux.com/PulseAudio")[/COLOR]

Reboot.

I hope this helps some of you out. It worked well for me, but I cannot make any guarantees.

That fixed some things but many apps still are broken.

These apps cannot make any sounds

XMMS
mplayer
vlc
(any ESD apps, including system sounds)

---

### Post by jjbean on 2007-05-16
> **ubnewbie2 said:**
> That fixed some things but many apps still are broken.

These apps cannot make any sounds

XMMS
mplayer
vlc
(any ESD apps, including system sounds)

Well I am still new at this so I am learning as I go. It is been a lot of Google and system breakage. My mplayer works so I cannot help with that one. 

Have you tried running the apps that do not work from the terminal?  Most of my problems were caused from missing plugins. Running in terminal might give you some hint as to the problem.

The only ESD sounds that don't work for me are the system sounds. Is your ESD enabled? Mine was disabled by default. I had to enable and reboot.

This is the website for pulse audio. You might be able to find something there.

[COLOR="Red"][http://pulseaudio.org/]("http://pulseaudio.org/")[/COLOR]

Like I said I am new at this. If I figure something else out I will post back.

---

### Post by futileissue on 2007-05-21
Turning off ESD worked for me immediately.  Thank you!

---

