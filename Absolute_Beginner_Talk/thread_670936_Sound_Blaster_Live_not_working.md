---
title: "Sound Blaster Live not working"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by zFb on 2008-01-18
Im brand new to Ubuntu (I have 7.10). When I first installed Ubuntu on my computer the sound played from my Sound Blaster Live card. For some reason now it will only play through my onboard. I want the sound to work on my Sound Blaster again... I've tried about everything i can find... Any help?

---

### Post by charleseddy on 2008-01-18
Of course, make sure your speakers are plugged into the correct card.  After that, go to System --> Preferences --> Sound Preferences, then change your Playback, Capture, and Mixer Track options to the Sound Blaster card (or Alsa).

Also, be sure that your card is seated properly.  Please reply if these steps don't work.

ce

---

### Post by zFb on 2008-01-18
Yea its already on SBLive 5.1 [sb0060] (Alsa mixer) and the sound is still comming through the onboard only.

---

### Post by biohypnotix on 2008-01-18
I have a first generation Sound Blaster Audigy [SB0090] and by default after installing Ubuntu I have no sound. My fix is to open up the Volume Control, go to Switches tab, and untick Analog/Digital output jack box. I have sound then. Not sure a regular Sound Blaster Live has the same options but worth a try if it does. If not, sorry I couldn't help.

---

### Post by c0met on 2008-01-18
When you  test you Soundblaster Live, do you disable the on-board soundcard in the BIOS?

---

### Post by rxbandit on 2008-01-18
> **biohypnotix said:**
> I have a first generation Sound Blaster Audigy [SB0090] and by default after installing Ubuntu I have no sound. My fix is to open up the Volume Control, go to Switches tab, and untick Analog/Digital output jack box. I have sound then. Not sure a regular Sound Blaster Live has the same options but worth a try if it does. If not, sorry I couldn't help.

This fixed my Audigy! :guitar:

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]

---

### Post by nikoPSK on 2008-01-18
Good, please mark this thread as "SOLVED"
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

nikoPSK

EDIT: oops, sorry thought rxbandit was thread op... :oops:

---

### Post by dastasha on 2008-01-20
I have a similar problem.
When I first installed gutsy 7.10, I found the login noise worked intermittently.
Didn't really bother me.
However, after installing flash to watch youtube video I found I have no sound.
Then it occurred to me I haven't heard the logon sound for a while either.

Tried the stuff in this thread with no success yet.
I'll be watching this one.

Edit: I know the sound blaster works as I switched over to windows and its fine.

---

### Post by SunnyRabbiera on 2008-01-20
eh well do keep in mind that ubuntu and windows are different OS's so what works in one might not work in the other...
but I hope you can get this resolved nonetheless

---

### Post by dastasha on 2008-01-20
Thanks, I'm sure I can resolve it one way or another because it worked originally. I've been listening to audio cd's and I watched the demo files on the default player when I first installed the system.

---

### Post by dastasha on 2008-01-20
Hmmmm... Just started working... I didn't change anything ...

---

### Post by zFb on 2008-01-26
Mine keeps switching about every other restart to which sound card wants to play sound...
I haven't disabled the onboard in the bios im doing that now and ill tell you what happens.

---

### Post by zFb on 2008-01-26
Well... I dont see the option in the BIOS to disable my onboard sound card. Though when i restarted it decided to play sound through my SB Live card. I've gone into the Volume -> Switched and unticked the digital/analog box sounds still playing through the card. Its seem s that when I first installed ubuntu 7.10 that it automatically picked up my SB Live card but when installed java to watch YouTube videos it started having problems and switched between the 2 cards. ( When I first installed Ubuntu i restarted several times without it switching between my onboard and SB Live card).

---

### Post by dastasha on 2008-01-27
Ok... digging in to my problem it now appears to me that it is not my onboard sound stopping the sound blaster from operating... I now suspect it is my TV tuner card. 
I blacklisted the onboard sound drivers and the problem is still there.
Getting closer...
There are other threads on this forum in a similar vein to this one.
I think the my TV tuner is being seen as another sound card. What else do you have in your pci slots?

---

### Post by dastasha on 2008-01-27
This is worth a look too -

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by dastasha on 2008-03-07
Disabled my onboard sound in BIOS.

All working fine for me now.

I should spend more time reading less time posting:-#

\\:D/

---

### Post by RefleXX on 2008-03-29
> **zFb said:**
> Yea its already on SBLive 5.1 [sb0060] (Alsa mixer) and the sound is still comming through the onboard only.
Thank you so much :)

---

