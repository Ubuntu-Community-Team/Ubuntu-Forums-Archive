---
title: "Master Volume Persists at Max"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by mlemily on 2007-10-02
Hi all,

This is an intermittent bug ever since I installed Feisty a couple days ago.

The master volume is set to max and can not be set to anything else.

When I click on the Volume control and drag the bar to any position, as soon as I let go it rises back up to the top (maximum)

Even more frustrating, there is a volume display window that appears in the bottom third of the screen, showing a full indicator bar, that persists over any appliction I may be working in, so I have to move things to see what's under it.

And something seems to be putting a big load on the cpu, when this is happening.
top at the command line gives load averages around 1  ick.
This also results in other applications being slow to non-responsive.

My guess is that this little display is supposed to flash, when you change the volume and then disappear, but now it persists, perhaps being rewritten constantly, as the windowing system seems pretty unhappy.

Double clicking on the speaker icon for volume to pull up the mixer window and working the master from there seemed to make no difference.

However the title bar of this window did contain the information about my hardware:
Intel 82801DB-ICH4 
(Alsa mixer)

This problem had disappeared after an overnight reboot, but reappeared when I tried to pull the volume down to mimium/mute.


Thanks for your help,
Emily

---

### Post by nowshining on 2007-10-02
have you tried clicking anywhere on the desktop.


Open up a terminal and type alsamixer and hit enter you can turn the volume up or down from there, also if you have a scroll whell mouse just hover it over the icon and sroll down to lower the volume and sroll up to raise the volume.

---

### Post by mlemily on 2007-10-03
Thanks for your reply!

I've tried both these suggestions and they have no effect.

These are both methods for adjusting the volume. 
When I use either of these methods for adjusting the volume I can bring it down a little, but as soon as I stop rolling the scroll button or hitting '-' the volume rises back to 100% all on its own.

And of course there is the volume indicator bar that persists in the bottom third of my screen.
No effect on this display either.

E.

---

### Post by nowshining on 2007-10-04
if the bottom third is what i think is what your trying to say then yes it's also on my side, also you should be able to click the icon to make it go away and double click to bring up the sound settings in GUI mode.

open up preferences - sound

and tell me what is selected / shown in the drop down menues - the one currently showing for all & not what's listed in the drop-down menu.

---

### Post by Xavier Oddmon on 2007-10-04
Hey, check your hotkeys, and try with a differnt keyboard. I had an old keyboard plugged in the other day (Old as in I needed an adapter to go to a PS2 port). It turned out it was constantly pressing Numlock and Volume Down, so I had the same (but opposite) effect. If this is the case, it could also be triggering that volume indicator you're talking about.

---

### Post by mlemily on 2007-10-05
Hi guys,

In response to the earlier post, under Preferences: Sound

The pull down menus display as follows - 

Sound Events:
Autodetect

Music and Movies:
Autodetect

Audio Conferencing -
Sound playback: ALSA, Advanced Linux Sound Architechture
Sound capture: ALSA, Advanced Linux Sound Architechture

Default Mixer Tracks- 
Device: Intel 82801DB-ICH4
Master Mono is now selected.
(it used to be Master, but I fiddled with it to see if it was an issue with controlling a particular channel)

At this point I've gone almost 48hrs without this behavior after a reboot where I let the computer sit overnight.
Intermittent is the worst kind of behavior.

I've come to the conclusion that this is a hardware issue, as the poster above suggests. Mainly because some of the behaviors I see in the rest of my windowing system, while I'm getting the wacky volume behavior look exactly like behavior I was seeing previously when using Suse.  Flickering pull down and display menus and an inablity to select from a pull down menu and sometimes display them, to be precise.
In ubuntu I've only seen this menu flicker behavior in Firefox, but in Suse I would see it in my Suse/Start menu most prominently.

Thanks for all your help!
E.

---

### Post by nowshining on 2007-10-07
it could also be butter fingers when using the mouse and or keyboard ;)

---

