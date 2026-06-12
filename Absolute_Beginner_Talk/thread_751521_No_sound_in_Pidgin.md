---
title: "No sound in Pidgin"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by astr0bomber on 2008-04-10
I am using Pidgin messenger, and I am the type of person who likes sounds for when I receive messages and when people come online. I went into the preferences and chose sound files for the sound effects and everything. Although, it's still not making any noise. I chose .wav files, assuming that everything can play .wav files. How come I am not getting any sound?

I have already downloaded and installed aplay and bplay, and tried using both of them under the sound preferences in Pidgin. Neither of them work at all. I have also tried selecting ALSA, without any luck. The only setting that works is "console beep". 

(btw I am using 7.10 Ubuntu)

---

### Post by alexforcefive on 2008-04-10
Does your sound work in general? Do you have Tools > Mute Sounds (in pidgin) checked? Do you have the right options enabled in Tools > Preferences > Sounds?

---

### Post by astr0bomber on 2008-04-10
For the most part, yes my sound works in general. It works sporatically, but that's a completely other issue all together. No, mute sounds in Pidgin is not on.

---

### Post by spiderbatdad on 2008-04-10
Pidgin gstreamer for sound. You need libgstreamer0.10-dev 
How do I get sound to work correctly? ¶

Pidgin uses gstreamer to play sounds. Playing sounds directly through esound or arts is no longer supported. To compile Pidgin with support for gstreamer you need libgstreamer0.10-dev and its dependencies. These packages are named differently on different platforms. If you do not wish to install these packages you can also just change your sound playing method in preferences to Command and use esdplay %s, artsplay %s, aplay %s, or play %s.
How do I make Pidgin use ALSA or OSS for playing sounds? ¶
What does the "Automatic" option do? ¶

The "Automatic" option lets gstreamer pick how the sounds are played. You can use the gstreamer-properties tool to control this if you use GNOME. 

[http://developer.pidgin.im/wiki/Using%20Pidgin](http://developer.pidgin.im/wiki/Using%20Pidgin)

---

### Post by astr0bomber on 2008-04-10
I have done all of that. I have the libgstreamer0.10-dev package, and I have tried the esdplay, artsplay, aplay and play options in Pidgin. None of this works. 

In my Ubuntu sound preferences, it uses ALSA for the mixer.

The only thing I haven't tried is the gstreamer-properties, which I do not know how to access.

---

