---
title: "[SOLVED] Master Audio Control GNOME"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-04-19
I guess this is a beginners question- its been an annoyance but not a high priority.

I have a problem with my keyboards volume control. Ubuntu recognizes my keyboard, and all of my buttons, but thats not my issue.

Whenever I hit Fn+ (Vol up) or (Vol Dn), the volume display on the screen pops up and shows a rise or fall, but it doesnt change my volume. If I open the volume control, I can see my volume up/down is controlling my Microphone volume, rather than PCM or front.

In KDE which I recently installed as a toy, its pretty easy. All you have to do is right click on the volume icon in the system tray, and select the master audio control channel. My volume works fine in KDE. GNOME presents no such options... Selecting PCM or front as the track to control on GNOME doesnt change anything, as the mic volume still changes.

Ive thought about using the gconf-editor, but I think Id have to make a script, and then of course my volume wouldnt visibly display on the screen...

Any ideas on getting the keyboard to control Front or PCM instead of Microphone?

---

### Post by h0ax on 2007-04-19
Have you tried System -> Preferences -> Keyboard Shortcuts ?

---

### Post by GSF1200S on 2007-04-19
> **h0ax said:**
> Have you tried System -> Preferences -> Keyboard Shortcuts ?

Yeah... like I said, my volume control works fine in terms of control.. my volume icon pops up on the display and shows me raising or lowering the volume. The only problem I have is that its controlling the microphone and not PCM or Front.

Weird huh?

---

### Post by Jussi01 on 2007-04-19
You need to remap the volume keys in gconf-editor. I cant tell you exactly how to do it right now cause im at uni on windows, but just type gconf-editor into terminal and have a look there... maybe someone else can shed more light than that....

---

### Post by GSF1200S on 2007-04-19
I took a look, but I didnt find anything pointing to the volume keys.

There are folders named sound, and even volume manager, but nothing seems to lead to changing the value of what my shortcut keys adjust.

I must be missing something...

---

### Post by sawjew on 2007-04-19
I had the same problem and it is very easy to fix in Feisty.  Go to your System>Preferences menu, select Sound.  In the sound preferences window down the bottom it says "Default Mixer Tracks".  Make sure the correct sound card is selected and select the track you want controlled.  The keyboard shortcuts should now control the right track.  :)

---

### Post by GSF1200S on 2007-04-19
> **sawjew said:**
> I had the same problem and it is very easy to fix in Feisty.  Go to your System>Preferences menu, select Sound.  In the sound preferences window down the bottom it says "Default Mixer Tracks".  Make sure the correct sound card is selected and select the track you want controlled.  The keyboard shortcuts should now control the right track.  :)

OMFG... dude, you make me feel like a moron.. problem resolved...

I never thought that it would be in sound- I kept thinking keyboard.. Thanks

---

### Post by puccha on 2007-04-24
was thinking in keyboard terms too, this fixed it. :) tx
now I can controll entire PCM instead of just my front speakers.

---

### Post by magicrobotmonkey on 2007-04-24
yea thats a hot tip right there. Thanks!

---

### Post by sckain on 2007-04-28
Yeah, I searched for some obscure conf file to edit, and the fix was super easy. T

HANKS!

:guitar:

---

### Post by mirzmaster on 2007-04-29
> **sawjew said:**
> I had the same problem and it is very easy to fix in Feisty.  Go to your System>Preferences menu, select Sound.  In the sound preferences window down the bottom it says "Default Mixer Tracks".  Make sure the correct sound card is selected and select the track you want controlled.  The keyboard shortcuts should now control the right track.  :)

I can't find an equivalent fix in Edgy.  Does anyone know how to resolve this issue in Edgy?

Thanks!

---

### Post by johneedoe on 2007-05-01
I'm also trying to find the answer w/ Dapper.  Any help would be great, I love using Ubuntu!

---

### Post by hanzomon4 on 2007-05-01
If you have a sound card like mine(m-audio delta 66) that splits the right and left channel in to two seperate channels you would have to use the softvol alsa plugin in the asound.conf

---

### Post by ZERO_SHIFT on 2007-10-21
I managed to get the volume control in Gutsy however the mute button does not mute the sound even though the signal says its mute.

Any ideas?

Thanks in advance

ThdwThassssdffg

---

### Post by GSF1200S on 2007-10-21
You have to set up your volume controls master channel. If your master channel is set to headphone or pcm, mute wont mute. Set the master channel to front, and then try mute.

---

### Post by ZERO_SHIFT on 2007-10-21
Where do I do this?

---

### Post by GSF1200S on 2007-10-21
> **ZERO_SHIFT said:**
> Where do I do this?
Try what sawjew said on the page before in this thread. That worked for me. Ive been on KDE awhile (this thread is old), so I cant remember the gnome way of doing things...

---

### Post by ZERO_SHIFT on 2007-10-21
> **GSF1200S said:**
> Try what sawjew said on the page before in this thread. That worked for me. Ive been on KDE awhile (this thread is old), so I cant remember the gnome way of doing things...

Check the screen shot, I cant find the "master volume your talking about"

Any ideas?

---

### Post by ZERO_SHIFT on 2007-10-21
I figured it out.

Apparently I have to highlight PCM & PCM-II both in order to be able to have full control of the sound.

Thanks for the help

Long Live The Community!!!

---

### Post by GSF1200S on 2007-10-21
Default Mixer Tracks at the bottom.. see how PCM is highlighted? Thats why your mute wont work.

Scroll down a little and look for "Master" or "front"- if you cant find either, tell me what the other options are...

---

### Post by GSF1200S on 2007-10-21
> **ZERO_SHIFT said:**
> I figured it out.

Apparently I have to highlight PCM & PCM-II both in order to be able to have full control of the sound.

Thanks for the help

Long Live The Community!!!

Haha, beat me to it :) Ill have to remember that- be sure to lend a hand if someone has a problem with this :)

Long live the community!!! :guitar:

---

### Post by wispygalaxy on 2007-10-21
Hi, I came here.  Where can I get sound preferences?  Maybe I can run a test....

EDIT: Testing right now,,,

---

### Post by kah00na on 2007-10-21
I thought getting the volume keys set to control things correctly on my HP dv8000 laptop would be a huge pain! NOT THE CASE thanks to two other users!! 

1.  sawjew who pointed me to the "Default Mixer Tracks" in the Sound Preferences...  Who would have thought to look for sound options there?  The Windows sound options are almost pointless.
2.  ZERO_SHIFT who suggested selecting BOTH the PCM and Master.  I didn't even know you could do that!  Now, not only does my volume work,  the mute button lights up when it is muted and shuts off when it's not!!

Wonderful.  I am running 7.10 Gutsy Gibbon.  Nice to know that these kinds of options have been carried forward through the releases.

---

### Post by Redenbacher on 2007-11-10
> I had the same problem and it is very easy to fix in Feisty. Go to your System>Preferences menu, select Sound. In the sound preferences window down the bottom it says "Default Mixer Tracks". Make sure the correct sound card is selected and select the track you want controlled. The keyboard shortcuts should now control the right track. 

You are a genius. Thank you.

---

