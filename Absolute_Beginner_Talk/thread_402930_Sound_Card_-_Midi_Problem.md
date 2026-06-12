---
title: "Sound Card - Midi Problem"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-04-06
Hi:
I've been trying to figure out why I cannot get any music notation program to be able to play the score.  I've just learned that midi is not working with my sound card - a sound blaster live.  I've also learned that when I installed Edgy, it has my card set up as an Ensoniq.

I have sound on my motherboard, and am thinking of trying that, but do not know how to go about disabling the blaster card, and enabling the onboard sound.  I don't even know what the onboard sound is.

I do get sound, just not midi.  I don't want to mess things up, but it would be nice to be able to get midi output working.  I used to use Finale in XP, but I cannot get Finale to run under wine.

Thanks,
Ziffnabb

---

### Post by Happy_Man on 2007-04-06
Same. Any help out there?

---

### Post by overdrank on 2007-04-06
> **ziffnabb said:**
> Hi:
I've been trying to figure out why I cannot get any music notation program to be able to play the score.  I've just learned that midi is not working with my sound card - a sound blaster live.  I've also learned that when I installed Edgy, it has my card set up as an Ensoniq.

I have sound on my motherboard, and am thinking of trying that, but do not know how to go about disabling the blaster card, and enabling the onboard sound.  I don't even know what the onboard sound is.

I do get sound, just not midi.  I don't want to mess things up, but it would be nice to be able to get midi output working.  I used to use Finale in XP, but I cannot get Finale to run under wine.

Thanks,
Ziffnabb

Hi if you have 2 sound cards install, onboard and the additional pci sound you can go to System,preference, and then sound and at the bottom of the page select you default sound card. Hope this helps. Good luck and welcome!

---

### Post by jem7v on 2007-04-06
MIDI isn't turned on by default in Ubuntu because a lot of modern sound cards don't, um, actually do their MIDI properly.

If you actually HAVE a hardware synthesizer (such as on a Sound Blaster Audigy) then [http://ubuntuforums.org/showthread.php?t=30963](http://ubuntuforums.org/showthread.php?t=30963) will probably help.

If you don't have a sound card with an actual hardware synthesizer onboard, you'll probably have to use something like "timidity," for which there are lots of instructions on these forums.

Oh, and if you can't get Finale to work at all, there Are other music editors for Ubuntu.  I'd suggest NoteEdit, personally, but if you're crazy (like me) you might be satisfied using text input with Lilypond...

---

