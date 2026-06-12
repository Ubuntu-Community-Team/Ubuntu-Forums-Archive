---
title: "Mic input won't play through speakers"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Picaroon on 2008-02-07
I run my Xbox sound through my laptop speakers, like this:
[XBOX] ---output----> [LAPTOP mic in] -----output----> speakers

I can record from the microphone, but I cannot get it so that the speakers play microphone sounds at all times.

In both the volume control panel and Alsamixer I have nothing muted, all boxes checked, and all volumes turned up. Again, I can use recorder just fine, but I cannot figure out how to make the input sound play through the speakers without using the recorder.

Thank you

---

### Post by K.Mandla on 2008-02-07
Perhaps I misunderstand, but isn't that the way it's supposed to work? In normal microphone use, if you ran that line straight to the speakers, you'd get hideous feedback. ... :shock:

Is there a line-in jack you can use instead?

---

### Post by Picaroon on 2008-02-07
Well, in Windows XP it plays all the time. That's how I do it in Windows. I like linux, but this is starting to get to me. I guess it's my sound input jack, it has a microphone logo.

---

### Post by BandD on 2008-02-07
Did you make sure that your mic PLAYBACK is unmuted?  Double click on the volume icon (or open the volume control) and on the PLAYBACK tab, make sure the mic setting is unmuted and turned up to the desired level.  

But yeah, if it's too loud you could get some serious feedback issues.

---

### Post by Picaroon on 2008-02-07
Ah, perhaps that is my problem. I don't have a microphone volume on my playback tab. Any ideas for getting it on there? I can't check a box for that--they're all checked.

One other thing: When I test the mic in the sound preferences, it comes through while testing.

---

### Post by BandD on 2008-02-07
That might be tricky.  

First try opening the volume control again and go to Edit--> Prefences.  In the box that opens make sure everything related to you mic is checked, and click ok.  Then look at the PLAYBACK tab again and see if it showed up.  

If that doesn't work, then the options are going to vary depending on your sound card.  And it gets kind of complicated.  

But try the prefences thing first and get back to us if that doesn't work.

---

### Post by Picaroon on 2008-02-08
I've done that. Everything is checked, unfortunately. I might just have to boot Windows when I want to play Halo.

Thanks for the help everyone

---

### Post by BandD on 2008-02-08
I just thought of something else.  

Try opening a Terminal and typing: ```
alsamixer
```

It'll bring up a graphical volume adjuster.  Make sure, if there are any mic settings in the playback section, that the mic values are unmuted and/or turned up.  It's worth a shot.  But if not, then yeah, it gets very tricky.

Good luck!

---

