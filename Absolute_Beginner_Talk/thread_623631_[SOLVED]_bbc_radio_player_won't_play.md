---
title: "[SOLVED] bbc radio player won't play"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-11-26
after a fresh installation of gutsy, bbc radio player won't play on firefox. i surf around this forum and install xine-plugin but still doesn't work (but the duration bar show it is playing, but i can't hear any sound). then i install mplayer-plugin but still doesn't work. i press the play button and the button won't pop-up again! (see screenshot). so difficult to get just a bbc radio player work on ubuntu!!

---

### Post by CatKiller on 2007-11-26
In the end I threw in the towel and installed RealPlayer. Even Helix won't do for some of their content.

Possibly the codec (Cook, is it?) is included in some other package but I gave up looking. I've got it somewhere though, because now I can use MPlayer on the command line to Listen Again.

---

### Post by gn2 on 2007-11-26
Install Real Player using these instructions for adding the commercial repo and using Synaptic: [https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods)

I would expect that all you would need to do would be tofollow the instructions for 7.04 but change the repo to:
_________ttp://archive.canonical.com/ubuntu **gutsy**-commercial main

If not use the other method.

You may also benefit from adding the MediaPlayerConnectivity plug-in for Firefox: 
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by afeasfaerw23231233 on 2007-11-27
after adding [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main and search realplayer in synaptic, all i got is this: kmplayer-konq-plugins

---

### Post by philinux on 2007-11-27
I had this working with totem but the controls were horrid. Tried gutsy reaplayer but there is a bug, it fails to install correctly the helix dna plugin required for bbc radio et all.

I solved this by using feisty's version of realplayer which correctly install the helix dna plugin.

[http://archive.canonical.com/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb](http://archive.canonical.com/pool/partner/r/realplay/realplay_10.0.9-0feisty1_i386.deb)

---

### Post by Blojic on 2007-11-27
I had the same problem - the solution's a lot easier than you think - the volume's muted in the BBC pleayer (you can see it on your screen dump).

Just turn it up!! It took me days too! Seems to always default to muted at launch.

Does anyone know how to change it?

Cheers,

Blojic

---

### Post by FuturePilot on 2007-11-27
It just took a while to buffer for me. I don't have Realplayer installed either. And yes the volume was muted by default :confused:

---

### Post by afeasfaerw23231233 on 2007-11-27
i was just thinking a method to get the bbc radio player work: i assign just 64MB RAM to my virtualbox to run win2000 and open ie or ff to play it! i forget the english idiom of it -- is it Make a mountain out of a molehill or Take not a musket to kill a butterfly? sorry for my bad english!
EDIT: should that be ''break a butterfly on the wheel''

---

### Post by afeasfaerw23231233 on 2007-11-27
Re: Blojic
how to turn the volume on? i thought that it was off also, but later i misunderstood the colourless volume bars meant it was 'fully-on''! it didn't go up when i press the volume bar or ''+'' button

---

### Post by mahiyar on 2007-11-27
I have mplayer and codecs installed, works fine in firefox.

---

### Post by afeasfaerw23231233 on 2007-11-27
i also tried mplayer but didn't work, the button didn't pop up again [see attachment]. did i miss the codec?

---

### Post by Blojic on 2007-11-27
> **afeasfaerw23231233 said:**
> Re: Blojic
how to turn the volume on? i thought that it was off also, but later i misunderstood it was 'fully-on'' as the volume bar doesn't show any colour! it didn't go up when i press the volume bar.

Your volume looks set to minimum to me. Just click the "+" button at the top a few times - the five bars under the button should go darker. (I've marked it on your screen dump).

Cheers,

---

### Post by Blojic on 2007-11-27
> **afeasfaerw23231233 said:**
> i also tried mplayer but didn't work, the button didn't pop up again [see attachment]. did i miss the codec?

Hi. The play button doesn't pop up for me either but it still plays okay (once I turn the volume up:)).

I'm a newbie and can't remember at the moment what I use to play BBC Radio player (Ubuntu Gutsy at home and I'm at work). I'll check later.

Cheers,

---

### Post by FuturePilot on 2007-11-27
> **afeasfaerw23231233 said:**
> i also tried mplayer but didn't work, the button didn't pop up again [see attachment]. did i miss the codec?

I don't think it's supposed to pop up. It didn't for me at least. It takes a while to buffer though, did you wait long enough?

---

### Post by Blojic on 2007-11-27
> **FuturePilot said:**
> I don't think it's supposed to pop up. It didn't for me at least. It takes a while to buffer though, did you wait long enough?

+1 on the buffering. It's a good minute or so (or seems like it!!)

---

### Post by afeasfaerw23231233 on 2007-11-27
thanks for your helpful quick reply!
i reinstall mplayer, follow your instruction and it works!
but i have another problem
when i press this [pic1], this [pop out] and it plays properly. i think it is a totem plugin. but somehow the voice is strange, a male voice appears to a female voice (and a bit like robot's voice) but that's not important as i seldom listen radio by this way

---

### Post by FuturePilot on 2007-11-27
Yes, that is the Totem plugin. If you would like to use the Mplayer plugin to at least see if it fixes the problem remove the Totem plugin
```
sudo apt-get remove totem-mozilla
```
If that doesn't work or you would prefer the Totem plugin you can reinstall it
```
sudo apt-get install totem-mozilla
```

---

