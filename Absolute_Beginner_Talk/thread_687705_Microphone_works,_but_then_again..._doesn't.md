---
title: "Microphone works, but then again... doesn't"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by Jinx-Wolf on 2008-02-04
So here's the thing.

I've got a Line In/Mic input, I've fiddled around and changed the input to Mic, and turned up the Mic volume, and also the Capture Feedback volume.

w00t, I can hear my voice cracking through my speakers now. However, when I try to launch Sound Recorder, I get this:

> 
Your audio capture settings are invalid. Please correct them in the Multimedia settings.


I'm not even really using it for the Sound Recorder, but the reason I tried Sound Recorder in the first place, is because it's not working in ANY application/game.

But with the Capture Feedback volume up, I can hear the feeback through the speakers...

Help? O.o

---

### Post by nol1ght on 2008-02-04
Try System->Perferences->Volume Control
Tab Options:

Put input source Line or Mic..

Tab Recording:
un mute all capture...

then try again...

---

### Post by Jinx-Wolf on 2008-02-04
Ok, so I tried to use the microphone under a different account.

The recorder came up, and I tried to record. It looked like everything was going well, but when I tried to play it back, it said "No Resource Found" or something to that nature.

I tried saving it and then playing it with MPlayer, but MPlayer gave a similar message as above. Banshee just didn't do anything.

I switched back over to this account and tried again, but it gave the same "Your audio capture settings are invalid" message.

Edit:

I've already tried all that, this is kind of a last ditch effort to get it working.
I've set it to Mic (Line-in causes the Capture feedback to even not work)
I've gone through and unmuted everything.
Still nothing...

Edit2:

Here's the output from the Terminal when trying to launch gnome-sound-recorder:
```

/home/wolf/.gtkrc-2.0:17: error: scanner: unterminated string constant - e.g. `style'

```

Which makes no sense, cause that file is for Pidgin...

---

### Post by Jinx-Wolf on 2008-02-05
Bump.

I took .gtkrc-2.0 out and tried again. The 'style' error went away, however it's still doing the same thing it did before.

I have used this mic on this computer before, and it has worked.

I'm out of ideas.

---

### Post by Jinx-Wolf on 2008-02-06
bump

---

### Post by Jinx-Wolf on 2008-02-06
No more ideas?

---

### Post by Jinx-Wolf on 2008-02-07
I'm giving this one more bump.

(I'm not quite sure, since it's been a few day. But I THINK it was having the exact same problem in Windows, so it might just be a hardware problem... but I still don't see why I would be able to hear the Feedback, but no apps would be able to record...)

---

### Post by Foomandoonian on 2008-03-05
It seems like every time I find a thread from someone with the same problem as me, it ends with an echo chamber of cries for help that go ignored. I guess some problems are not popular. :(

---

