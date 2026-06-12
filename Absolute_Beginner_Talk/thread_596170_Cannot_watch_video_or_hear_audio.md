---
title: "Cannot watch video or hear audio"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by willako on 2007-10-29
I am new to Linux and just installed Ubunto 7.10. I have added a Windows codec.
I have downloaded RealPlayer for Linux but I do not really know what I am doing.
I keep getting error messages when I try to play video.
Help...

---

### Post by swisscow on 2007-10-29
Go to add/remove programs - search for ubuntu restriced extras in the multimedia section and install it.

Try your sound / video again. I fyou still have problems go back to add / remove and install vlc.

Then try again

If still not working - search the forums.

Best of luck

---

### Post by philinux on 2007-10-29
you need to follow these instructions.

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by sneezymelon on 2007-10-29
have you installed the reqd codecs??

---

### Post by willako on 2007-10-29
Thanks all.

1. Go to add/remove programs - search for ubuntu restriced extras in the multimedia section and install it.

Try your sound / video again. I fyou still have problems go back to add / remove and install vlc.

I tried the above but I could not see vic.


have you installed the reqd codecs??
How can I find out what the required codecs are, as I have looked.

---

### Post by philinux on 2007-10-29
VLC is just one player. 

Did you have a look at the thread I posted about Enabling Multimedia.

Attached add/remove screenshot showing VLC.

---

### Post by SunnyRabbiera on 2007-10-29
the best way to get all the codecs is to use automatix:
[here]("http://www.getautomatix.com/")

---

### Post by willako on 2007-10-29
vlc and the others are installed and I looked at the link all those I have already installed but I still get errors

---

### Post by philinux on 2007-10-29
Which site - one at a time, what your trying to play and what errors.

Have to deal with this logically. (Automatix is not recommended) I've managed to get everything sorted from synaptic or add/remove.

---

### Post by unisol on 2007-10-29
i have no problem with sound in gutsy, but in etch i could not get any sound until i typed esd at the command prompt. from then on i had sound. give it a try.

---

### Post by willako on 2007-10-29
Which site - one at a time, what your trying to play and what errors.

I just tried Automatix and still nothing.

Mainly BBc for radio and video, aswell Channel 4 on Demand.

---

### Post by unisol on 2007-10-30
try this:

sudo apt-get install module-assistant
 sudo m-a update
 sudo m-a prepare
 sudo m-a a-i alsa
 Reboot and setup your sound settings

---

### Post by willako on 2007-10-30
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
Reboot and setup your sound settings

This I have done, sound settings are they ones in preferences?

I still get errors when trying to play realplayer streams:
Error   The Playerdoes not have the capabilities to play back this content.
           The following components are required -   text/html

This is using Helix player.
 
I installed esd  but still get no sound.

---

### Post by swisscow on 2007-10-31
I've had problems with the bbc streaming stuff as well.

Solved it by adding the firefox add-on media player connectivity

I've set it to use vlc for the beeb stuff

When you click a video on bbc news just choose windows media player (not real player) in the preferences then click the film strip icon. VLC opens and plays the video.

Try it - if vlc isn't happy, try another player in the media player connectivity settings. If no luck you'll be no further along I'm afraid, but also no further back.

---

### Post by philinux on 2007-10-31
All you need for embedded audio is to install realplay from synaptic. It includes the needed firefox plugin

Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.630 built with gcc 3.3.5 on Aug 6 2007

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes

---

### Post by Hairy Hobbit on 2007-10-31
Hello all.

I am having trouble here too.  

Philinux, is this something I do through the package installer?  

Thanks,
HH

---

### Post by willako on 2007-10-31
Same question from me as Hairy Hobbit as i cannot see them in Synaptic or add/remove?

---

### Post by philinux on 2007-10-31
you need to follow these instructions

[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

---

### Post by Hairy Hobbit on 2007-10-31
It still doesn't work.

When I go to the bbc web page Firefox still prompts me to chose XVINE or the other one, and then buffers to 50% and stops.

So I still cant use real player to stream or watch video clips off websites.  My lack of sound looks like its to do with a driver issue with my Toshiba laptop sound card.

I think Ubuntu is going to stay as a dual boot with XP just as something to play with - I cant replace XP with it yet.  I love the idea, I love the principal - but for me it just isn't working.  There's so many things in this thread and others that people have very generously suggested I try but all it means is another reinstall back to a clean system (which I dont mind doing - just so I know what works and is repeatable).

Maybe I should leave it a month or two.  Do these sort of issues get ironed out in between 6 monthly releases?  I hear the toshiba sound thing has been around for a couple of versions at least.

Thanks for trying though!
HH

---

### Post by philinux on 2007-11-01
You can have too many plugins, can you post what you got in 

```
about:plugins
```

you could try the extension mediaplayerconnectivity

also in edit prefs content configure file handling you can specify the app for default

---

### Post by willako on 2007-11-01
1

---

### Post by willako on 2007-11-02
1

---

### Post by willako on 2007-11-02
1

---

