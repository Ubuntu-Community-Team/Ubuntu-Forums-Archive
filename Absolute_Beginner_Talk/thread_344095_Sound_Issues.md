---
title: "Sound Issues"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2007-01-22
Ok, so I have 2 issues with sound that I need to have delt with.

First: The keyboard shortcuts that adjust volume. (IE: Mute, Volume up, and Volume down) Control the Master Volume. The master volume however, does not seem to contrtol anything, as i can mute it, and i still get sound. The one thing that DOES seem to work, is PCM volume. So there are 2 things I need to figure out.
         One: Is there a way to make the Master Volume work? It seems odd that it doesnt.
                 Or
         Two: Is there a way to change the shortcut so that it controls PCM volume instead of the master volume?

Second: My second problem is more annoying than the first. When I reboot my computer, sometimes (I'd liek to say 50% of the time, but sometimes its more often than that.) I will get no sound. I then have to reboot the computer again, and continue doing so, until it suddenly gives me sound. I haven't the slightest idea what could be causeing this problem.

Anyone have any suggestions on what to do, look at, etc... for either of the above issues?

(Note: I have searched and searched in the forums, and as of yet have not found a single thread to fix either of these issues.)

---

### Post by ComplexNumber on 2007-01-22
> First: The keyboard shortcuts that adjust volume. (IE: Mute, Volume up, and Volume down) Control the Master Volume. **The master volume however, does not seem to contrtol anything**, as i can mute it, and i still get sound. The one thing that DOES seem to work, is PCM volume. So there are 2 things I need to figure out.not in your case it doesn't. if you haven't alread, add the volume applet to your panel by right clikcing on the panel and selecting 'add to panel'. then right click on the volume applet when its on the panel and select 'preferences'. change it to 'Master'(ir master volume).


as for your second problem, i have a haunch what it may be. reboot your computer and go into the bios. disable the inbuilt soundcard. then, i want you to go to synaptic and install alsamixer. once installed, open alsamixer and one of the far right hand controls should be the volume of your inbuilt sound card. turn that right down (on mine, its "AC97").

---

### Post by bladefallcon on 2007-01-22
> **ComplexNumber said:**
> not in your case it doesn't. if you haven't alread, add the volume applet to your panel by right clikcing on the panel and selecting 'add to panel'. then right click on the volume applet when its on the panel and select 'preferences'. change it to 'Master'(ir master volume).

That doesnt help at all. All that does is make it so that the volume icon in the system tray controls the master volume. But master volume still doesnt effect the volume of anything.

> as for your second problem, i have a haunch what it may be. reboot your computer and go into the bios. disable the inbuilt soundcard. then, i want you to go to synaptic and install alsamixer. once installed, open alsamixer and one of the far right hand controls should be the volume of your inbuilt sound card. turn that right down (on mine, its "AC97").

See now the problem with this one is that if i turn off my onboard sound card...then i wont get any sound. I am using that as my sound card. I do not have a sound card installed in my computer as of right now.

---

### Post by ComplexNumber on 2007-01-22
originally, i thought it may be to do with the inbuilt sound card interfereing with the main sound card.

ok, in alsamixer, click on File in the menu, then 'preferences'. what does it give for your possible 'mixer names and visability'? which one is ticked?

---

### Post by bladefallcon on 2007-01-22
There are three options: 

VIA 8237 (Alsa Mixer)
SAA7134 (Alsa Mixer)
C-Media Electronics CMI9761 (OSS Mixer)

The first is the one selected. I have tried switching to the other 2, but they do nothing. I mute them, still get sound. Turn them up, nothing....turn them down...nothing...they have no effect..

I can say that when running windows, I had software Installed from C-Media that seemed to control the volume quite well. (even let me use it as 5.1 suround sound.)  Don't know if that info will help...but i hope it will

---

### Post by ComplexNumber on 2007-01-22
right, lets try something else then. go to main menu -> system -> preferences -> sound. on the device tab, make the various sound drivers in  'sound events' and 'music & movies'. i think it would probably bes best if they were set to use alsa by default. now click on the 2nd tab, enable 'sound sound mixing (ESD)'. 

also, [this]("http://ubuntuforums.org/showthread.php?t=205449") may help.

---

### Post by bladefallcon on 2007-01-22
> **ComplexNumber said:**
> right, lets try something else then. go to main menu -> system -> preferences -> sound. on the device tab, make the various sound drivers in  'sound events' and 'music & movies'. i think it would probably bes best if they were set to use alsa by default. now click on the 2nd tab, enable 'sound sound mixing (ESD)'.


Ill check out that link...as for the rest...there is no device tab there...and 'software sound mixing (ESD)' is already enabled.

---

### Post by bladefallcon on 2007-01-22
Ok...heres an interesting tidbit...I used the 
```
aplay -l
```

and this was my output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 2/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Why would it list the same device twice (as though there were 2 of them) and with different subdevices???

---

### Post by ComplexNumber on 2007-01-22
> **bladefallcon said:**
> Ill check out that link...as for the rest...there is no device tab there...and 'software sound mixing (ESD)' is already enabled.
no Device tab? hmmm thats sounds a bit worrying. i think that could be a clue. fire up your terminal and tell me what the printout gives you (eg errors etc) when you type in 'gnome-sound-properties'. i'm wondering if you may need to install some alsa packages.

what about when you go to main menu -> system -> preferences -> multimedia systems selector. do you have both audio and video tabs there?



> **bladefallcon said:**
> Ok...heres an interesting tidbit...I used the 
```
aplay -l
```and this was my output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 2/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Why would it list the same device twice (as though there were 2 of them) and with different subdevices???
mines listed 3 times, so i dont think thats anything to worry about.

---

### Post by bladefallcon on 2007-01-22
> **ComplexNumber said:**
> no Device tab? hmmm thats sounds a bit worrying. i think that could be a clue. fire up your terminal and tell me what the printout gives you (eg errors etc) when you type in 'gnome-sound-properties'. i'm wondering if you may need to install some alsa packages.

All that does is open up the same thing as System> Preferences> Sound. Still no device tab.

> what about when you go to main menu -> system -> preferences -> multimedia systems selector. do you have both audio and video tabs there?


Umm...there is no Multimedia Systems in System> Preferences

---

### Post by ComplexNumber on 2007-01-22
well thats worrying that you don't because you should have.

fire up synaptic and do a search for "alsa" on name only. do you have the following installed:
alsa-base
alsa-utils
alsa-tools
alsa-source (not too sure about this)
libesd0-alsa




given the information that you've presented so far, i'm sure there must be enough clues now for someone more knowledgable about sound/audio than me that will be able to point you in the right direction. i recently had a sound problem that i solved myself, so i'm just going over the same ground with you as i did.

also, did you go through [this]("http://ubuntuforums.org/showthread.php?t=205449")? if so, what was the outcome?

---

### Post by bladefallcon on 2007-01-22
> **ComplexNumber said:**
> well thats worrying that you don't because you should have.

fire up synaptic and do a search for "alsa" on name only. do you have the following installed:
alsa-base
alsa-utils
alsa-tools
alsa-source (not too sure about this)
libesd0-alsa




given the information that you've presented so far, i'm sure there must be enough clues now for someone more knowledgable about sound/audio than me that will be able to point you in the right direction. i recently had a sound problem that i solved myself, so i'm just going over the same ground with you as i did.

also, did you go through [this]("http://ubuntuforums.org/showthread.php?t=205449")? if so, what was the outcome?



Yes all of those are installed. As for trying the stuff in that link, that is all for when i have no sound...each time iv rebooted today, the sound has worked...so i'll have to wait til it stops again to try those things...

---

### Post by ComplexNumber on 2007-01-22
> **bladefallcon said:**
> Yes all of those are installed. As for trying the stuff in that link, that is all for when i have no sound...each time iv rebooted today, the sound has worked...so i'll have to wait til it stops again to try those things...
just curious, but do you find that when the sound works that you can see the 'Devices' tab in gnome-sound-properties?

---

### Post by bladefallcon on 2007-01-22
> **ComplexNumber said:**
> just curious, but do you find that when the sound works that you can see the 'Devices' tab in gnome-sound-properties?

Couldnt tell ya...iv never looked at it when the sound didnt work...Iv always just rebooted..and continued doing so until the sound worked.

---

### Post by geetarista on 2007-01-27
I've been having the same exact problem that you had, and all of a sudden I got it to work.  I'm not sure exactly what I did but I opened up Alsa mixer by right-clicking on the volume icon and then clicked "open volume control".  Once you have that opened, go to edit > preferences and then check everything in there.  Once I had that opened, I just played around with everything and all of a sudden my sound was working properly.

Hope this helps!!

By the way, I'm using a Sony Vaio VGN-FS980.

---

