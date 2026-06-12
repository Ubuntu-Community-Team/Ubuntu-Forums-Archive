---
title: "HP Notebook, mute turns on at boot and stuck on"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by mdsmedia on 2006-09-10
I've got a HP Compaq nx6120. I've had Dapper installed since about July and Breezy and Hoary before that since October. It seems after the last batch of updates it happened that when I boot Ubuntu my mute button lights up and won't let me switch it off. The volume switch on the desktop works ok...mute switches on and off but I still get no sound. I wonder if it's a switch in the updates which might have tripped it up? Any ideas?

---

### Post by mdsmedia on 2006-09-11
Lets try putting this another way.

I downloaded the auto updates the other day, on my HP Compaq nx6120.

The notebook has 3 volume control buttons on the keyboard. UP, DOWN and MUTE.

If I boot into Windows XP there is no problem (not with sound anyway :)). When I boot into Ubuntu, the light on the mute button is off through most of the boot process, then before I get to the login screen the light on the mute button comes on.

If I press the volume UP or DOWN buttons the mute light stays on. I don't have any sound in Ubuntu, but the indicator on the screen shows the volume going up or down, respectively.

I can click on the volume control on the desktop and it will respond, but there is still no sound.

Is there somewhere I can go to trip this control in Ubuntu?

---

### Post by matth45 on 2007-07-10
mdsmedia, or anyone else - did you ever find a solution to this problem?  I have the same issue with an hp pavilion tx 1000.  The sound chip is 

```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

and it (the chip) can be muted and unmuted in the alsamixer, but there's no sound from the speakers and the "muted" light on the mute button stays on.

---

### Post by mdsmedia on 2007-07-10
> **matth45 said:**
> mdsmedia, or anyone else - did you ever find a solution to this problem?  I have the same issue with an hp pavilion tx 1000.  The sound chip is 

```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

and it (the chip) can be muted and unmuted in the alsamixer, but there's no sound from the speakers and the "muted" light on the mute button stays on.No, I never found a solution to this. I reinstalled Ubuntu and all was fine.

---

### Post by anewguy on 2007-07-10
I don't know if this will help you or not, as my sound is from a different manufacturer, but I had to do the following:

-open up the alsa mixer by double-clicking on the speaker  on the upper bar
-click edit and preferences
-find "external amplifier" and put a check by it
-go back to the main alsa mixer page
-click on the switches tab
-uncheck "external amplifier"

It seems counter-intuitive to me, but I found this in another post and it works great for my laptop!
Hope it might help you!:)

---

### Post by zakirs on 2007-07-11
well my pc is hpcompaq v3239 well it has also a similar prob lem  when i boot to ubuntu thte sound wont come at all even if i play any audio file

---

### Post by mirosol on 2008-05-08
I know i'm a year late on this one, but still.. Here's the solution for mute button on most HP laptops. ...Just in case that someone is looking for an answer and stumbles on this thread..

Fix is simple.

```
gksu gedit /etc/modprobe.d/alsa-base
``` 

..and add this to the end of file

```
options snd-hda-intel model=hp
```

Should work for most of HP laptops.

---

