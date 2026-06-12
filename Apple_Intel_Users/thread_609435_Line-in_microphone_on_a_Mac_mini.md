---
title: "Line-in microphone on a Mac mini?"
date: 2007-11-10
forum: Apple Intel Users
---

### Post by jslmg on 2007-11-10
Has anyone here gotten an external mic to work in Ubuntu through the line-in jack on a Mac Mini?

I have a static mic running through an amplifier; the amp is plugged into the line-in jack. This works great in Mac OS X, of course, on everything from Audacity to Skype, but I haven't yet found the way to get Ubuntu to pick up the sound from that line-in jack.

I specify "line in jack" here, cuz I found this thread about getting it to work with a mic/headphone combo in Skype: [http://ubuntuforums.org/showthread.php?t=566524&highlight=skype](http://ubuntuforums.org/showthread.php?t=566524&highlight=skype)

I've made all the preference settings recommended in that thread, but I think that thread doesn't really address the issue I have.

Any help? Any config files to look at? Drivers needed?

---

### Post by arolin on 2007-12-03
I am also having problems getting my microphone/line in to work in Ubuntu with my mac mini.

Sound output works fine,

When I try to start the sound recorder I get the following:
**[INDENT]Your audio capture settings are invalid. Please correct them in the Multimedia settings.[/INDENT]**

When I got to **System>>Preferences>>Sound Preferences ** the Test of the Sound Capture device under Audio Conferencing always fails.

Any help? Any config files to look at? Drivers needed?

Thanks,
Amaury

---

### Post by entangled on 2008-01-01
I've tried the sound recorder on Gutsy on my Intel Mini and got the same problem, no microphone sound.
The microphone works well in Macosx, spoken commands work and skype works.
In Gutsy I get sound test output to headphones.
In Gutsy when I try to speak into the microphone I get a background hiss (live?), but no sound in headphones, and I can record a sound file. Playing the sound file just reproduces the hiss. 
Looks like a low-sensitivity input - but it works on Macosx. 
Perhaps the sound card (SigmaTel STAC9221 A1) has a high-sensitivity mode that Ubuntu is not setting? 
Perhaps I need a signal booster?

---

### Post by entangled on 2008-01-14
One other point, since having no luck with microphone input on Gutsy I tried the same microphone in the same machine with Suse103. It works immediately. Perhaps it's because Suse uses kde and krecorder rather than gnome-recorder?

---

### Post by cyberdork33 on 2008-01-14
> **entangled said:**
> One other point, since having no luck with microphone input on Gutsy I tried the same microphone in the same machine with Suse103. It works immediately. Perhaps it's because Suse uses kde and krecorder rather than gnome-recorder?more likely a difference in the underlying audio system, ALSA.

---

### Post by entangled on 2008-01-19
I wonder if anyone is still interested in this? I've tried many combinations of settings and at last it's working.
I am using Ubuntu 7.10 with gnome-sound-recorder and a directly connected Z=50k microphone ( AT9170).

In sound-recorder you record from either Capture or from Digital (it doesn't seem to matter)

In gnome-volume-control you set the following

Under 'Recording' tab: 
Capture can be any level but must be enabled (no red crosses)
Digital should be high level (100%) and must be enabled.

Under Options' tab:
Input Source is Line

So Capture must be on but Digital seems to control the actual level of input. The volume I get seems OK.

Also I found that if krecord was running it stopped gnome-sound-recorder from working. 
Hope it works for you.

---

### Post by jslmg on 2008-01-20
> **entangled said:**
> I wonder if anyone is still interested in this? I've tried many combinations of settings and at last it's working.
Ooh! Yes, very much so!

> I am using Ubuntu 7.10 with gnome-sound-recorder and a directly connected Z=50k microphone ( AT9170).

In sound-recorder you record from either Capture or from Digital (it doesn't seem to matter)

In gnome-volume-control you set the following

Under 'Recording' tab: 
Capture can be any level but must be enabled (no red crosses)
Digital should be high level (100%) and must be enabled.

Under Options' tab:
Input Source is Line

So Capture must be on but Digital seems to control the actual level of input. The volume I get seems OK.

Also I found that if krecord was running it stopped gnome-sound-recorder from working. 
Hope it works for you.

I'll try this soon and let you know how I fare with it.

---

