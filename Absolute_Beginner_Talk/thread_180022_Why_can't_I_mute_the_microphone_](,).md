---
title: "Why can't I mute the microphone? ](*,)"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by [censored] on 2006-05-21
I'm on Breezy 5.10, using the standard ALSA drivers with OSS emulation wrapper.

For some reason I can't set it up so that the microphone can still be used to record, but won't broadcast through the speakers as it does so. At the moment, if I try to record some guitar piece I've been studying on the computer, I get feedback which is annoying. 

In the Volume Control panel, on the Capture tab, I have the microphone muted. But it doesn't seem to have any effect.

I want to be able to record, but not have what's going into the mic automatically come out of the speakers.

---

### Post by halfvolle melk on 2006-05-21
Try typing "alsamixer" in a terminal. There you'll see all the channls. <- and -> switch channels, up and down increase/decrease volume and "m" troggles a channel on and of. "Esc" quits aslamixer.

---

### Post by [censored] on 2006-05-21
Thanks but I just tried alsamixer. pressing or unpressing "m" has no effect.

---

### Post by oscar on 2006-05-21
I think you need the microphone muted, not just in the capure tab but also the Playback tab, to get it there, Edit > Preferences and tick Microphone.

---

### Post by [censored] on 2006-05-23
Hi Oscar. Microphone is already ticked in Preferences, and clicking the little icons at the bottom (a little mic, and what appears to be a speaker) does squatt. The only thing that has any affect is the Capture bar. That will kill the mic completely, but I actually want to record without having what I'm recording amplified through the speakers.

---

### Post by CompShrink on 2007-07-08
does anyone have a solution for this? I am having the same problem: mute is working like a litteral "mute," reducing the sound to min volume, but not making it silent.

The problem is MythTV delays the sound to sync it with the video, but the mic and line in sounds cannot be muted in the alsa mixer, so I end up getting the immediate sound that doesn't sync, AND the MythTV delayed sound both playing on top of each other, like a wierd echo, and the video's synced to the later echo.

When I mute the mix, it goes to min volume, not silent. If i unmute it I can adjust the volume up and down, but again, not to silent.

Thanks for any help.

---

### Post by forrestcupp on 2007-07-08
Try going back to alsamixer
```
alsamixer
```
In alsamixer there is a Playback screen and a Capture screen.  Press F3 to make sure you are in Playback.  Probably nothing changed because it usually comes up in Playback mode.  On this screen, find the "mic" selection and turn the volume down all of the way.

Now press F4 to get to the Capture screen.  Find the "mic" selection here, and turn the volume slider up.

This will give you volume for the capture, but not playback.

Some sound cards use "m" for mute, and some don't.  On the ones that don't, you just have to turn the volume slider down all the way.

---

