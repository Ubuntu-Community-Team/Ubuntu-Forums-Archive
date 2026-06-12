---
title: "Audio/Video Player for Linux"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by patanjali on 2006-04-15
Having downloaded RealPlayer 10GOLD I seem to have ended up with a cutdown version with limited functionality.  I then looked through the players that come with Ubuntu, and they also seem to have limited functionality.  Can anyone point me in the direction of a player that has all or most of the functionality of realPlayer for Windoze?

Thanks

Patanjali ](*,)

---

### Post by Perfect Storm on 2006-04-15
Try with VLC and/or Mplayer
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by bionnaki on 2006-04-15
I like xine/gxine

---

### Post by OffHand on 2006-04-15
[QUOTE=bionnaki]I like xine/gxine[/QUOTE]
Me too. And I think Realplayer sucks.

---

### Post by Bloch on 2006-04-15
VLC is great at everything - except in the looks department.
I use amarok, which plays mp3, ogg, wma and the apple mac format (whatever that extension is) Amarok is resource-hungry however.
But if you like a particular player you could consider converting your audio files as a batch to a format (presumably ogg or mp3) supported by your player.

---

### Post by Perfect Storm on 2006-04-15
> VLC is great at everything - except in the looks department.
It's mistakenly compiled with gtk1.2 instead of gtk2. It's with gtk2 in dapper or compiling itself with --enable-gtk2 can also do the trick or if you're KDE user --enable-qt

---

### Post by DavidFourer on 2006-04-17
I just installed mplayer plugin for firefox with Synaptic Package Manager, and it's working.  I would not say the video is perfectly smooth but the sound and picture are very clear.  That's nice.  Also, It's automatic.  I click on a video link on a web page and the video starts instantly.  One click and that's it.

Should I install mplayer stand-alone ?  I don't know if I need it.  If so, do I want mplayer-386 or mplayer-586?  --386 was installed with the plugin by the Synaptic Package Manager but I have not tried to use it alone--don't really know what it's for.

On the same topic, Perhaps someone can explain what Codecs and Windows Codecs are.

---

### Post by Perfect Storm on 2006-04-17
mplayer-386 = Optimized for 386, 486 and up.
mplayer-586 = Optimized for pentium and up
mplayer-686  = Optimized for pentium 4 and up

Windows Codecs or w32codecs is something you need to play multimedia files, that may be the reason your video isn't playing smoothly. The reason it isn't included is because it's non-gpl.

---

### Post by bionnaki on 2006-04-18
this is a good guide: [http://ubuntuforums.org/showthread.php?t=75817](http://ubuntuforums.org/showthread.php?t=75817)

---

