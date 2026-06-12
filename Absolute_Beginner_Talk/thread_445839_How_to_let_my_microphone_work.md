---
title: "How to let my microphone work?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by rover on 2007-05-16
I have this nice headset. I hear every sound verry clearly, but i my friends do not hear me over teamspeak. (I got all settings right on the program and no, i'm not muting my microphone )

So, it is plugged in, now how to let this thing work? :) 

Any commando's or something?

---

### Post by Kobalt on 2007-05-16
Try to open your volume controler then press of File > Change Devices > Analog : (OSS Mixer). Search for your mic : is it in the list ? Make sure it's selected here first, then test it in Ekiga for example.

---

### Post by jjalocha on 2007-05-16
Many people have (many different) problems with microphone input in Ubuntu. Here is one possible solution. Hope it helps to you. If not, search the forums. It's full of posts. Post your hardware.

[http://ubuntuforums.org/showthread.php?t=418396](http://ubuntuforums.org/showthread.php?t=418396)

---

### Post by rover on 2007-05-16
But where is my volume controler? *blush*

Edit: i'm still working with Badger ;/

---

### Post by byenary on 2007-05-16
type alsamixer in console
or gnome-volume-controler
Or click on the speaker on the right top of your screen ?

---

### Post by rover on 2007-05-16
alsamixer = no options to click on

Gnome volume thingy, no response.

The speaker on the right isn't there

---

### Post by Kobalt on 2007-05-16
Then you can add it with a right-click to your panel : Add to the panel > System and Settings > volume control

---

### Post by lakersforce on 2007-05-16
> **rover said:**
> But where is my volume controler? *blush*

Edit: i'm still working with Badger ;/

Perhaps you should consider to upgrade to at least Dapper.

---

### Post by jjalocha on 2007-05-16
If you follow the link I posted before, and go the 'alsamixer' route, you will have to use your [COLOR="Red"]keyboard[/COLOR].

> 
From the command line, you can use alsamixer. Use [COLOR="Red"]TAB[/COLOR] for selecting the 'Playback', 'Capture' or 'All' window, and use [COLOR="Red"]LEFT/RIGHT[/COLOR] to select the desired control. You have to make sure you get the following settings right (all of them):
[LIST]
[*]All channels must be non-zero (use [COLOR="Red"]UP/DOWN[/COLOR]).
[*]'Capture' must be enabled (use [COLOR="Red"]SPACE[/COLOR]).
[*]Select the correct 'Input Source' if you have more than one. (I only have 'Mic'.)
[/LIST]


The screenshots show you how it should turn out.

I know, this solution sounds awkward, but in many cases, 'alsamixer' for some mysterious reason seems to be the only solution that works.

There have also been some success reports with the graphical KDE mixer tool (which you can install in Gnome, too). I don't remember if it's called 'kmix'?

---

