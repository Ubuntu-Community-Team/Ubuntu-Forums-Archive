---
title: "Help my 3 year old Linux hacker"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by jjf on 2006-04-10
My three year old daughter is a more proficient computer user than my parents.  Since she can type her name and type "cat," she's able to log in to her user account on my Ubuntu Thinkpad and play tuxpaint and other gcompris games.  Being curious and not at all afraid to try new buttons and see what they do, she picked up the basics in just a few minutes.  (e.g., I told her how to get a new sheet to paint on: click this button, then click the green check mark.  "What happens if I click the red one?"  Try it and see.  "Oh, it goes away."  Meaning the dialog box asking to discard the old image and get a fresh page.)  8)

But TuxPaint is crashing on me every time.  I see the splash screen, then it just closes.  

When I launch it through the terminal, I see this warning before it launches:
```
Warning: I could not set up audio for 44100 Hz 16-bit stereo.
The Simple DirectMedia Layer error that occurred was:
No available audio device
```
My audio works fine for every other program.

After tuxpaint crashes, I see this error message returned in the terminal:
```
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
```

Any help would be greatly appreciated, and would make a little girl's day.  :D

---

### Post by ubernoob on 2006-04-10
Aww! When i hear stories like that, my heart goes all warm, and i want a kid myself. :)  Unfortunately i can't help you with your problem.

Edit: you might want to try reinstalling libsdl. It might help.

---

### Post by Kimm on 2006-04-10
Sounds like you have a sound problem...

before you open TuxPaint, type this in terminal:

sudo lsof | grep dsp

and look for output. If some other application is using your soundcard TuxPaint may not be able to use it.
I still cant see how that would make it crash though...

---

### Post by mips on 2006-04-10
jjf,

Sorry can't help with your problem. Remember you asking about laptops and just wondering how you find the thinkpad ?

---

### Post by jjf on 2006-04-10
I love the Thinkpad (T23), mips, thanks.  Most everything worked right out of the box, with the notable exceptions of wireless and printing.  But after a few hours of tinkering and forum hunting, I got those working, too.  It took about a month to iron out all the little problems that crop up in my typical usage pattern, but now that I have I'm surprised to find Ubuntu just as pleasant to use as OS X.  And it interfaces better with the Windows boxes at work, so that's very nice.

Kimm, I typed what you told me and then ran tuxpaint from terminal.  This time I did not get any warning about sound, and when the tuxpaint splash screen came up, I heard its chime.  But it still immediately closed, and returned the same error message:

```
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
```

re. reinstalling libsdl: I searched synaptic and came up with quite a list of packages that have libsdl in them somewhere.  Apparently the basic libsdl1.2debian comes in five flavors: alsa, arts,  esd, nas, oss.  I have libsdl1.2debian-oss.  Do I need the others, perhaps?

---

### Post by az on 2006-04-10
What graphics card are you using?


"Warning: I could not set up audio for 44100 Hz 16-bit stereo.
The Simple DirectMedia Layer error that occurred was:
No available audio device"

try (from a terminal)
killall esd
tuxpaint

If it works, you should try the Dapper live cd and install tuxpaint on that.  The bug may already be fixed in dapper.

---

