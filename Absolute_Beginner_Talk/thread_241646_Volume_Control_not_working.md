---
title: "Volume Control not working"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Teamster on 2006-08-22
I have a Logitech G15 keyboard. Now, I know that there are no specific drivers for it, but the volume control wheel is puzzeling. When I spin it, or mute the volume, it registers on the screen, but the sound from the computer remains at a the same volume. the only way I can get the volume to change is through the little icon with the dial and arrows, the Volume Panel. It's annoying me, can anyone help please?

---

### Post by seanUSXIII on 2006-08-30
Bump.

I'm having the same problem. Is there a way to fix this and retain the OSD?

Thanks,
Sean

---

### Post by Toxicity999 on 2006-08-30
What it looks like to me is that your keyboard is controlling a sound system you don't use. Where it should be controlling master it might be controlling PC Speaker or headphone for example. I don't think you
'll find an answer unless there is some kind of configuration options for that keyboard. Try double clicking the Sound apple on the Panel. Now watch it as you use the sound dial. See what it moves. If it's muted, unmute it. Go from there.

---

### Post by sredman on 2006-08-30
I am having much the same problem... the Volume "knob" on keyboard seems to control the master Ubuntu volume according to the onscreen volume sliders, bu the actual sound level does not change. 
The Master volume control right now only seems accessible through Gxine. The slider in GXINE controls sound output from all other apps.  The volume sliders in apps are ultimately subordinate to the GXINE slider.  

How i see my need is, How the HECK do I get my master volume control off of GXINE and back to ALSA???](*,) ](*,)   
Seeing as this is my only really nagging problem now, i have little to complain about.
Any help would be appreciated...

---

### Post by sredman on 2006-08-30
> **Toxicity999 said:**
> Try double clicking the Sound apple on the Panel. Now watch it as you use the sound dial. See what it moves. If it's muted, unmute it. Go from there.
When I do this, it controls the master volume sliders. I can in fact Mute it onscreen without affecting the volume at all.

Fiddling while writing this, the GXINE volume slider moves with the PCM Slider.
hope that helps

---

### Post by seanUSXIII on 2006-08-31
Mine controls the center volume. BTW i have a 5.1 card but am currently using stereo and have the speakers hooked into "front". The slider controls "Center/LFE", should the speakers be plugged into center?

---

### Post by Toxicity999 on 2006-08-31
Well my sound is weird as well like with headphones that master control isn't so... masterful could be much the same for you. Maybe your sound is routed solely through PC Speaker which may not be affected by master... As for playing with what does what with the who. Talk to someone else honestly was just trying to dig some info out for anyone with more broad knowledge of how to fix it, and not just what the problem is.

---

### Post by Seryozha on 2006-09-08
I am having a similar problem.  I have a plantronics digitial headset and when i use the volume control on the cord it does nothing.  when i change the slider on the panel it also does nothing.  I have to double slick the sound icon on the panel and change the volume there in the master.  any ideas?

---

### Post by Kevkill on 2007-02-13
I am also having a similar problem. When I use my volume control buttons on my laptop (Acer TravelMate 2313) the on screen display comes up and moves but the sound does not change. When I double click on the volume slider icon in the taskbar I can see that the master volume is being controlled but the sound does not change. The only way I can change my volume is by adjusting the headphone slider up / down.
Is there any way to re map the headphone and master sliders?

Thanks,
-Kev

---

### Post by trevor98 on 2007-02-16
Same problem here, the volume slider (controlled directly or from the keyboard hot keys) is irrelevant.  The problem I identified in the Volume Control dialog box is that the master volume control does not effect the PCM controls.  If I change the PCM slider itself then the output volume changes.  How do I make the master volume slider actually control the speaker volume?

---

### Post by hanexar on 2007-02-16
I always had this problems.

Actually in alsa mixer, the master control have no effect at all, and I'm controling sound with the PCM controls. I had this problems on all the ubuntu installs I made on this box.

---

### Post by wvuhotrod on 2007-02-17
So I how do you change the device the master volume contols?  Mine contols the SiS SI7012 and I need it to control my SB Live 5.1 SB0220?  Thanks a bunch.

---

### Post by Harvs on 2007-03-02
Sames problem here. The volume and mute control on my keyboard control the master volume. But sound is going through the PCM control and I have to use ALSA to control the volume on screen.

I've done loads of searching, but can't find any solution....

---

### Post by jegerjensen on 2007-03-30
I have the same problem.  It looks like many have this issue.

In this thread there is a rather informed discussion, but still no solution:
[http://gnomesupport.org/forums/viewtopic.php?t=10879](http://gnomesupport.org/forums/viewtopic.php?t=10879)

---

### Post by hanexar on 2007-04-20
Here's how I fixed my problem: [http://ubuntuforums.org/showpost.php?p=2495954&postcount=5](http://ubuntuforums.org/showpost.php?p=2495954&postcount=5)

---

### Post by tombott on 2007-07-27
> **hanexar said:**
> Here's how I fixed my problem: [http://ubuntuforums.org/showpost.php?p=2495954&postcount=5](http://ubuntuforums.org/showpost.php?p=2495954&postcount=5)

Many thanks for this, it's worked a charm.
This has been doing my head in for ages!

---

### Post by GatorV on 2008-04-27
Wow thanks, I was getting a little frustrated after my upgrade, thanks a bunch!

---

