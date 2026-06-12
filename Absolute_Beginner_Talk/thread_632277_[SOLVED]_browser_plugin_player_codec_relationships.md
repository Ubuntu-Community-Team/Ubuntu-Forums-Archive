---
title: "[SOLVED] browser plugin player codec relationships"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2007-12-05
I wanted to title this "Seeking Wisdom and Understanding" because that's what I want, but if I did that nobody could find the answers but me.... 

Seems like I'm always running into browser/plugin/player/codec relationships. If I just understood how they worked I could better help myself. So ...

1. What is the difference between a media player and a media player plugin? Can a browser call either one? 

2. What establishes the connections between media players and codecs? 

3. Where do codecs live?

4. If I get a browser dialog box asking me what I want to use to play something, and nothing's on the list, even though I know I've installed one or more, how do I find them? This question may fall under the general rubric of "how does one locate the executable file for a program? I can get lists of all the files for, say, xmms*, but how do I know which one to direct the browser to?

Can anyone suggest a good reading/starting point for understanding how Ubuntu Linux handles these things? Inquiring minds want to know ...

Gary

---

### Post by Hospadar on 2007-12-05
1) they are usually two seperate packages for example totem (the default media player for gnome) has the "totem" package, and the "totem-mozilla" (that might not be the exact name, but it's close"  mplayer and vlc have similar setups.  the plugin is a "wrapper" for the main program that just picks out what it needs

2) It depends on the media player, some (mplayer, vlc) have their codecs built in (I believe) but totem uses separate codec packages (the gstreamer codecs) or if you choose to use them, the xine codecs (install "totem-xine" to do so, on the user end, gstreamer and xine behave exactly the same way in terms of installation and use, but have low-level differences you generally needn't worry about)

3) generally the actual library files will be in /usr/lib somewhere, but you shouldn't worry about that, all you need to do is install them from synaptic (seach for "gstreamer" or "xine" depending on which you are using, if you arn't sure, just look at which one has a bunch installed, and which one has none installed)

4) executables are generally going to be located in /usr/bin if you are having difficulty locating one, open up synaptic, go to the package in question (be it totem, mplayer, etc) right-click->preferences->installed files.  Look for the file in a */bin/<whatever> location.  the actual executable will generally be named after the package and have no file extension.

hope this helps!

Also, if you are trying to play windows (wmv) video or realplayer video, you'll need the medibuntu repositories (just google medibuntu) and if it's flash videos, you'll need flash player (the "nonfree" one), in which case just search synaptic by name for "flash"

---

